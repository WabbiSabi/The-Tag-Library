# RFID Pre-Print Tag Fulfillment — Quality Control Template

> Standardize quality control for every Gamma lab pre-print order. This template guides the operator through order intake validation, production monitoring, post-production QA, and packaging/shipment sign-off — ensuring no order ships without documented proof of accuracy. Modeled after the phased deployment approach in the Vega Deployment Strategy: each stage has defined ownership, validation checkpoints, and escalation paths.

---

## Order Details

| Field | Value |
|---|---|
| Customer / Event Name | |
| Store ID(s) | |
| Event Date(s) | |
| Tier Classification | ☐ Tier 1  ☐ Tier 2  ☐ Tier 3 |
| Service Model | ☐ Model A (Full-Event)  ☐ Model B (Launch-Day)  ☐ Model C (Audit) |
| Order Submitted By (MerchOps) | |
| Order Received Date | |
| Ship-By / Need-By Date | |
| QC Performed By | |
| QC Completion Date | |

---

## Stage 1 — Order Intake Validation

**Owner:** Contractor (with MerchOps escalation path)
**SLA:** Validation complete OR escalation filed within 4 hours of order receipt

### 1.1 Catalog Completeness Checklist

- [ ] All SKUs in order have a valid UPC
- [ ] Every UPC resolves in Amazon Print Solution (APS)
- [ ] Product title matches UPC for every line item
- [ ] Price per item confirmed against customer catalog
- [ ] Tag type specified per SKU (M8 Sticker / M8 Hang-Tag / Midas Flag-Tag / Bling 1/2/3 / Flag Tag 4 / Starport M730)
- [ ] Quantity per SKU confirmed with 10% blank buffer applied
- [ ] Material-specific notes reviewed (F&B items, metallic packaging, condensation-prone, irregular shapes)
- [ ] Any bespoke tagging requirements flagged and confirmed with MerchOps

### 1.2 Catalog Gap Log

> ⚠️ If any items fail validation, document below and escalate to MerchOps immediately. Production does NOT begin on incomplete orders.

| SKU / Item | Issue | Escalated To | Date/Time Escalated | Resolution | Date Resolved |
|---|---|---|---|---|---|
| | | | | | |
| | | | | | |

### 1.3 Order Summary (confirmed after validation)

| Field | Value |
|---|---|
| Total SKUs in Order | |
| Total Tags to Print (incl. 10% buffer) | |
| Total Blank Buffer Tags | |
| Tag Type Breakdown | M8 Sticker: __ / M8 HT: __ / Midas Flag: __ / Bling: __ / Starport: __ / Other: __ |
| Estimated Production Hours | |
| Printer(s) Assigned | |
| Ink Rolls Required (est.) | |

### 1.4 Intake Sign-Off

| Validator | Date | Catalog Complete? (Y/N) | Production Authorized? (Y/N) |
|---|---|---|---|
| | | | |

---

## Stage 2 — Production Monitoring

**Owner:** Contractor
**Reference:** Gamma lab effective throughput ~550–625 tags/hr per printer (accounts for ink changes, alignment checks, SKU changeovers). Raw throughput ~1,200 tags/hr per printer.

### 2.1 Pre-Production Equipment Check

- [ ] Printer(s) powered on and calibrated
- [ ] Ink ribbon seated correctly (verify latch into divot — ref: Cosmic JAX Issue #1)
- [ ] Blank tag stock loaded and sufficient for full order + buffer
- [ ] Test print executed: 3 tags from first SKU — confirm alignment, readability, EPC encoding
- [ ] Test tags scanned with RFID scanner — confirm EPC reads correctly
- [ ] APS print template confirmed (correct tag type, correct print layout — ref: PGA "F1 TEMP" disappearing template incident)

### 2.2 Production Run Log

> One row per SKU or per print batch. Track start/stop times to identify throughput issues.

| SKU / UPC | Tag Type | Qty Ordered | Qty Printed | Printer Used | Start Time | End Time | Ink Roll Changes | Issues / Notes |
|---|---|---|---|---|---|---|---|---|
| | | | | | | | | |
| | | | | | | | | |
| | | | | | | | | |

### 2.3 Mid-Run Checks

> Perform every 500 tags or every SKU changeover, whichever comes first.

| Check # | Time | Print Alignment OK? | EPC Encoding OK? | Ink Quality OK? | Tag Stock Level | Notes / Corrective Action |
|---|---|---|---|---|---|---|
| | | | | | | |
| | | | | | | |

### 2.4 Production Issues Log

| Issue | Time Identified | Impact (tags affected) | Corrective Action Taken | Resolved? (Y/N) | Escalated To |
|---|---|---|---|---|---|
| | | | | | |
| | | | | | |

### 2.5 Common Production Failure Modes (reference)

| Failure Mode | Action |
|---|---|
| VOID prints | Check laser eye alignment, ink ribbon tension, tag stock compatibility. At O2, VOID prints triggered a SEV2. |
| Print template missing | Confirm APS template exists before starting. At PGA, a temp template disappeared overnight with 3+ hrs no on-call response. |
| Ink ribbon pull-out | Verify ribbon is latched into divot, not free-spinning on spindle. |
| Lopsided printing | Recalibrate printer; check tag stock alignment guides. |

---

## Stage 3 — Post-Production Quality Assurance

**Owner:** Contractor
**Target:** ≥98% pre-print fulfillment accuracy (correct UPC-to-tag mapping, no VOID prints shipped)

### 3.1 Spot-Check Sampling

> Minimum sample: 5% of total order OR 50 tags, whichever is greater.
> Sampling method: Pull tags from beginning, middle, and end of each SKU's print run.

| SKU / UPC | Sample Size | Tags Scanned (RFID) | EPC Valid? | UPC-to-Tag Mapping Correct? | Print Quality | VOID Tags Found? | Failures Found | Notes |
|---|---|---|---|---|---|---|---|---|
| | | | | | | | | |
| | | | | | | | | |

### 3.2 QA Failure Handling

> If ANY of the following are found, the affected SKU batch must be reprinted before packaging:

- [ ] Incorrect UPC-to-tag mapping (wrong product encoded)
- [ ] VOID prints in sample
- [ ] Unreadable EPC (scanner cannot read tag)
- [ ] Misaligned print (QR code or barcode not scannable)
- [ ] Wrong tag type used for SKU

### 3.3 QA Failure Log

| SKU | Failure Type | Qty Affected (est.) | Reprinted? (Y/N) | Reprint Qty | Re-QA Passed? (Y/N) |
|---|---|---|---|---|---|
| | | | | | |
| | | | | | |

### 3.4 F&B Tag Verification

> Required if order contains food & beverage items. Refer to the F&B Tagging SOP for visual placement guides.

**Tagging Rules (from F&B SOP):**
- [ ] F&B tags include human-readable title OR color-coded category identifier
- [ ] Tag type matches material-specific recommendation (ref: tag-material compatibility matrix)
- [ ] Material-specific application guidance document is printed and will be included in shipment
- [ ] If Midas Flag-Tags: confirm adhesive side is correctly oriented on tag sheet

**F&B Placement Requirements:**

| Product Type | Placement Rule |
|---|---|
| Hot & cold products | Flag Tags only — never use any other RFID tag type |
| Cans | Tag at top of body so sensor sits above, not on the container |
| Bottles | Tag at top of body so sensor sits above, not on the container |
| Foil products | Tag at top edge so sensor sits above, not on the container |
| Cans / bottles (general) | Never place tags on lids or body where sensor rests on product |
| Metal surfaces | Never apply tags directly to metal where sensor rests on product |

> ⚠️ Keep all tags and tagged products at least 6 ft (1.83 m) away from the checkout gate.
> ⚠️ When a product is returned, replace the tag before moving it back to the sales floor.

### 3.5 QA Summary

| Metric | Value |
|---|---|
| Total Tags QA'd (sample) | |
| Total Failures Found | |
| Failure Rate (%) | |
| All Failures Resolved? (Y/N) | |
| QA Pass? (Y/N) | |

---

## Stage 4 — Packaging & Shipment Preparation

**Owner:** Contractor (delivery coordination transitions to Amazon in Phase 1–2, contractor in Phase 3+)

### 4.1 Packaging Checklist

- [ ] Tags separated and packaged by SKU
- [ ] Each SKU package clearly labeled: Customer Name / Event / SKU / UPC / Quantity / Tag Type
- [ ] Blank buffer tags (10% of order) packaged separately and labeled "BUFFER — BLANK"
- [ ] Material-specific tag application quick-guides included (photo-based, 1-page per tag type)
- [ ] F&B application guidance included (if applicable)
- [ ] QA summary sheet included in shipment (copy of Stage 3 results)
- [ ] Shipment manifest created with photo of packaged contents

### 4.2 Shipment Manifest

| SKU / UPC | Tag Type | Qty in Package | Package Label Verified? (Y/N) |
|---|---|---|---|
| | | | |
| | | | |
| Blank Buffer Tags | Mixed / ______ | ______ | ☐ |

| Inclusion | Status |
|---|---|
| Application Quick-Guides Included | ☐ Yes  ☐ N/A |
| F&B Guidance Included | ☐ Yes  ☐ N/A |

### 4.3 Photo Manifest

- [ ] Photo taken of all labeled packages before sealing
- [ ] Photo taken of sealed shipment with external label visible
- [ ] Photos attached to order tracking record

### 4.4 Delivery Details

| Field | Value |
|---|---|
| Delivery Method | ☐ Hand-Carry  ☐ Ground Ship (3–5 days)  ☐ Overnight  ☐ Other: _______ |
| Carrier / Courier | |
| Tracking Number | |
| Ship Date | |
| Expected Delivery Date | |
| Destination Address | |
| Receiving POC (Name + Phone) | |
| Backup POC (Name + Phone) | |

---

## Stage 5 — Order Close-Out & Metrics

**Owner:** Contractor submits; MerchOps reviews

### 5.1 Order Completion Summary

| Milestone | Date/Time |
|---|---|
| Order Received | |
| Production Start | |
| Production End | |
| QA Complete | |
| Ship Date | |
| Total Calendar Days (receipt → ship) | |
| Total Contractor Hours | |

### 5.2 Quality Metrics

| Metric | Value | Target |
|---|---|---|
| Total tags printed | | |
| Total tags shipped (excl. waste) | | |
| VOID / waste tags | | < 2% of total |
| QA sample size | | ≥ 5% of order |
| QA failure rate | | < 2% |
| Catalog gaps escalated | | 0 (ideal) |
| Catalog gaps resolved before production | | 100% |
| Reprints required | | 0 (ideal) |

### 5.3 Consumables Tracking

| Field | Value |
|---|---|
| Ink Rolls Used | |
| Blank Tag Stock Consumed (incl. waste) | |
| Remaining Blank Tag Stock at Gamma Lab | |
| Reorder Needed? (Y/N) | |

### 5.4 Escalation Summary

| Field | Value |
|---|---|
| Total Escalations Filed | |
| Escalation Details | (ref: Stage 1 Gap Log + Stage 2 Issues Log) |
| Average Escalation Resolution Time | |
| Unresolved Items at Ship | ☐ None  ☐ See notes: _______________ |

---

## Sign-Off

| Role | Name | Signature / Approval | Date |
|---|---|---|---|
| QC Operator (Contractor) | | | |
| MerchOps Reviewer | | | |

---

## Additional Notes

| Date | Who | Details |
|---|---|---|
| | | |
| | | |

---

## Reference: Escalation Paths

| Issue Type | First Contact | Escalation | SLA |
|---|---|---|---|
| Catalog gap / missing UPC | MerchOps | IM/LM | 4 hours from order receipt |
| Printer hardware failure | On-site troubleshoot (power cycle, recalibrate, swap backup) | RIOT | 5 min troubleshoot → swap to backup |
| APS template missing / broken | AEG on-call | IM/LM | Document printer serial + template name |
| Tag stock / ink resupply needed | Pre-authorized reorder (below threshold) | Managerial approval (above threshold) | Same-day for in-stock items |
| VOID prints (systematic) | Recalibrate; check laser eye alignment | RIOT if persists after recalibration | Stop production until resolved |
| EPC encoding failure | Verify APS config; test with alternate tag stock | AEG on-call | Stop affected SKU until resolved |
