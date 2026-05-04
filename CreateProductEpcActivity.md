package com.amazon.ihm.vega.merchant.experience.service.activity

import com.amazon.coral.annotation.Operation
import com.amazon.coral.annotation.Service
import com.amazon.coral.service.Activity
import com.amazon.declarativelambdametrics.annotations.Applies
import com.amazon.declarativelambdametrics.annotations.CountMetric
import com.amazon.declarativelambdametrics.annotations.FailureMetric
import com.amazon.declarativelambdametrics.annotations.FailureMetrics
import com.amazon.declarativelambdametrics.annotations.SuccessMetric
import com.amazon.declarativelambdametrics.annotations.TimeMetric
import com.amazon.ihm.id.Barcode
import com.amazon.ihm.id.Gtin
import com.amazon.ihm.id.StoreId
import com.amazon.ihm.rfidcodes.translate.GTINToEPCTranslator
import com.amazon.ihm.rfidcodes.utils.NumberUtils
import com.amazon.ihm.vega.merchant.experience.CreateProductEpcInput
import com.amazon.ihm.vega.merchant.experience.CreateProductEpcOutput
import com.amazon.ihm.vega.merchant.experience.IhmSherlockATRecoverableException
import com.amazon.ihm.vega.merchant.experience.IhmSherlockATUnrecoverableException
import com.amazon.ihm.vega.merchant.experience.InvalidInputException
import com.amazon.ihm.vega.merchant.experience.ItemIdType
import com.amazon.ihm.vega.merchant.experience.service.dao.DDBProductEpcRecoverableException
import com.amazon.ihm.vega.merchant.experience.service.dao.DDBProductEpcUnrecoverableException
import com.amazon.ihm.vega.merchant.experience.service.dao.IProductEpcDAO
import com.amazon.ihm.vega.merchant.experience.service.dao.PutProductEpc
import com.amazon.ihm.vega.merchant.experience.service.util.ServiceConstants
import com.amazon.ihm.vega.merchant.experience.service.util.ServiceConstants.CREATE_PRODUCT_EPC_ACTIVITY
import com.amazon.ihm.vega.merchant.experience.service.util.ServiceConstants.CREATE_PRODUCT_EPC_OPERATION
import com.amazon.ihm.vega.merchant.experience.service.util.ServiceConstants.SERVICE_NAME
import com.amazon.ihm.vega.merchant.experience.service.util.ServiceConstants.VALID_GTIN_LEN
import com.amazon.retry.RetryPolicy
import com.amazon.retry.RetryingCallable
import com.amazon.retry.policies.ExponentialBackoffRetryPolicy
import com.amazonaws.services.s3.AmazonS3
import com.fasterxml.jackson.databind.JsonNode
import com.fasterxml.jackson.databind.ObjectMapper
import mu.KotlinLogging
import java.security.SecureRandom
import java.time.Instant
import javax.inject.Inject

@Suppress("ThrowsCount")
@Service(SERVICE_NAME)
class CreateProductEpcActivity @Inject constructor(
    private val ddbProductEpcDAO: IProductEpcDAO,
    private val epcTranslator: GTINToEPCTranslator,
    private val amazonS3Client: AmazonS3,
) : Activity() {

    private val logger = KotlinLogging.logger { }
    private val secureRandom = SecureRandom()

    companion object {

        // Min is starting from 30... because AD has its printing ranges starting sequentially from 10... & 20...
        private var serialNumberMinValue = ServiceConstants.SERIAL_RANGE_START

        // Max is taken from the EpcTranslator library as that is the max value of serial number it supports
        private var serialNumberMaxValue = ServiceConstants.SERIAL_RANGE_END
        private const val VALID_GTIN_LENGTH = ServiceConstants.VALID_GTIN_LEN
        private const val VALID_UPC_LENGTH = ServiceConstants.VALID_UPC_LEN
        private val OBJECT_MAPPER: ObjectMapper = ObjectMapper()
        private const val MAX_ATTEMPT_TO_GENERATE_BATCH_EPC = 2000
        /**
         * ExponentialBackoffRetryPolicy is used for retrying IhmSherlockATRecoverableException
         * @see RetryingCallable
         */
        private val clientRetryPolicy: RetryPolicy = ExponentialBackoffRetryPolicy.Builder()
            .withRecoverableThrowables(IhmSherlockATRecoverableException::class.java)
            .withBackoffCoefficient(1.5)
            .withMultiplierMillis(200)
            .withMaxDelayMillis(15000)
            .withMaxAttempts(8)
            // this is important because the interceptor means that you'll get an InvocationException
            // instead of the Exception you want to retry
            .withCheckNestedThrowables(true)
            .build()

        private val validBarcodeTypes = listOf(
            ItemIdType.UPC,
            ItemIdType.UPC_E,
            ItemIdType.EAN,
            ItemIdType.EAN8,
            ItemIdType.PLU,
            ItemIdType.GTIN,
        )
        private val validEpcPattern = Regex("^[A-F0-9]{24}$")
        private val validPluPattern = Regex("^([0-9]{3,8})$")
    }

    /**
     * Creates the specified number of EPCs on providing storeId, GTIN and Barcode
     */
    @Operation(CREATE_PRODUCT_EPC_OPERATION)
    @CountMetric
    @SuccessMetric
    @TimeMetric(applies = Applies.ALWAYS)
    @FailureMetrics(
        value = [
            FailureMetric(
                failureClasses = arrayOf(InvalidInputException::class),
                name =
                "$CREATE_PRODUCT_EPC_ACTIVITY.$CREATE_PRODUCT_EPC_OPERATION.InvalidInputException",
            ),
            FailureMetric(
                failureClasses = arrayOf(IhmSherlockATRecoverableException::class),
                name =
                "$CREATE_PRODUCT_EPC_ACTIVITY.$CREATE_PRODUCT_EPC_OPERATION.IhmSherlockATRecoverableException",
            ),
            FailureMetric(
                failureClasses = arrayOf(IhmSherlockATUnrecoverableException::class),
                name =
                "$CREATE_PRODUCT_EPC_ACTIVITY.$CREATE_PRODUCT_EPC_OPERATION.IhmSherlockATUnrecoverableException",
            ),
        ],
    )
    @Suppress("LongMethod")
    fun createProductEpc(input: CreateProductEpcInput): CreateProductEpcOutput {
        if (input.storeId.isNullOrEmpty() ||
            input.quantityOfEpc == null ||
            input.itemIdWithTypeList.isNullOrEmpty()
        ) {
            throw InvalidInputException(
                "CreateProductEpc input have null/empty values for storeId, quantityOfEpc or itemIdTypeWithList",
            )
        }
        logger.info("Received get product request with input $input")

        val domain: String = ServiceConstants.getEnvOrProperty(ServiceConstants.DOMAIN)
        if (domain == ServiceConstants.GAMMA) {
            populateSerialRangeForGammaEnv()
        }

        return RetryingCallable({
            try {
                /* Check if GTIN is present in the list, if yes, use it to create EPC, else, create GTIN from PLU */
                val gtinList = input.itemIdWithTypeList.filter {
                    it.idType == ItemIdType.GTIN && it.itemId.length == VALID_GTIN_LENGTH
                }
                val gtin = when (gtinList.isEmpty()) {
                    true -> Gtin(createGtin(input))
                    false -> Gtin(gtinList.first().itemId)
                }
                logger.info("Gtin for request : $gtin for input : $input")
                val barcode = Barcode(
                    input.itemIdWithTypeList.filter {
                        validBarcodeTypes.contains(it.idType)
                    }.first().itemId,
                )

                val productEpc = PutProductEpc(
                    gtin = gtin,
                    barcode = barcode,
                    storeId = StoreId(input.storeId),
                    timestamp = Instant.now(),
                )
                val epcList = createEpcList(input.quantityOfEpc, productEpc)
                logger.info { "epcList for storeId : ${input.storeId} is : $epcList and gtin is $gtin" }
                return@RetryingCallable CreateProductEpcOutput.builder().withEpcList(epcList).build()
            } catch (e: NoSuchElementException) {
                throw InvalidInputException(
                    "itemIdTypeList does not contains either GTIN or Barcode in the provided input",
                    e,
                )
            } catch (e: IllegalArgumentException) {
                throw InvalidInputException(
                    "CreateProductEpc input does not contains correct GTIN, StoreId or barcode",
                    e,
                )
            } catch (e: DDBProductEpcUnrecoverableException) {
                throw IhmSherlockATUnrecoverableException(
                    "Failed to add created list of EPCs in ddb for" +
                        "given storeId: ${input.storeId}, itemIdTypeWithList: ${input.itemIdWithTypeList}",
                    e,
                )
            } catch (e: DDBProductEpcRecoverableException) {
                logger.error(e) { "Recoverable error occured while adding EPCs in ddb" }
                logger.info { "Retrying creating the product EPCs" }
                throw IhmSherlockATRecoverableException(
                    "Error occurred while trying to add the list of EPCs in ddb " +
                        "for given storeId: ${input.storeId}, itemIdTypeWithList: ${input.itemIdWithTypeList}",
                    e,
                )
            }
        }, clientRetryPolicy).call()
    }

    fun createGtin(input: CreateProductEpcInput): String {
        var gtin = ""
        val upcList = input.itemIdWithTypeList.filter {
            (it.idType == ItemIdType.UPC || it.idType == ItemIdType.UPC_E) && it.itemId.length == VALID_UPC_LENGTH
        }
        val pluList = input.itemIdWithTypeList.filter {
            it.idType == ItemIdType.PLU && validPluPattern.matches(it.itemId)
        }

        if (!upcList.isEmpty()) {
            gtin = upcList.first().itemId.padStart(VALID_GTIN_LEN, '0')
        } else if (!pluList.isEmpty()) {
            gtin = NumberUtils.getGtinFromPlu(pluList.first().itemId)
        }
        return gtin
    }

    @Suppress("TooGenericExceptionCaught")
    private fun populateSerialRangeForGammaEnv() {
        val bucketName = "gamma-us-west-2-sherlock-config-bucket"
        val fileName = "serial-range-config.json"
        try {
            val returnedPayload = amazonS3Client.getObjectAsString(bucketName, fileName)
            if (returnedPayload != null && !returnedPayload.isEmpty()) {
                val laneConfigStr: JsonNode = OBJECT_MAPPER.readTree(returnedPayload)
                serialNumberMinValue = laneConfigStr.get("start_range").toString().toLong()
                serialNumberMaxValue = laneConfigStr.get("end_range").toString().toLong()
            }
        } catch (e: Exception) {
            throw InvalidInputException("Exception occurred in reading epc serial range config: ${e.message}", e)
        }
    }

    @Suppress("TooGenericExceptionCaught", "SwallowedException")
    private fun createEpcList(quantity: Int, productEpc: PutProductEpc): List<String> {
        val epcList = mutableListOf<String>()
        var count = 0
        while (epcList.size < quantity && count < MAX_ATTEMPT_TO_GENERATE_BATCH_EPC) {
            count += 1
            val epc = epcTranslator.translate(
                productEpc.gtin.toString(),
                secureRandom.nextLong(serialNumberMinValue, serialNumberMaxValue).toString(),
            )
            logger.info { "Serial range start : $serialNumberMinValue, Serial range end : $serialNumberMaxValue" }
            if (!validEpcPattern.matches(epc)) {
                throw IhmSherlockATUnrecoverableException(
                    "Translated EPC from GTINToEPCTranslator didn't match the required pattern. Created EPC: $epc",
                )
            }
            if (ddbProductEpcDAO.putProductEpc(epc, productEpc)) {
                epcList.add(epc)
            }
        }
        if (count == MAX_ATTEMPT_TO_GENERATE_BATCH_EPC) {
            logger.error { "Max attempt to generate batch EPC reached and need to clear generate epc's from database" }
            throw IhmSherlockATUnrecoverableException(
                "Failed to generate required EPCs after $MAX_ATTEMPT_TO_GENERATE_BATCH_EPC attempts",
            )
        }
        return epcList
    }
}
