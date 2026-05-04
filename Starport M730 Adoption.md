# Starport M730 (Tageos241) — Program Adoption

**Tag Designation:** Starport M730 / Tageos EOS-241  
**Spec Sheet:** StarportM730aka EOS-241-M730-PET_42x16_240_198_196_197-013.1.pdf  
**Status:** Recommended for official adoption as a supported tag type  
**Gamma Intake SIM:** https://issues.amazon.com/issues/P326962592  
**AEG TT for support:** https://t.corp.amazon.com/P307284589  

---

## Purpose

This document recommends the formal adoption of the Starport M730 (Tageos241) as an officially supported RFID tag within the Vega program. The M730 has completed exploratory evaluation, ML baseline testing, and production validation at NA-AA-90. It is no longer an experimental tag — it has proven field performance and addresses critical supply chain, cost, and operational gaps. This document outlines the case for moving the M730 from exploratory status to an officially offered tag type for customers.

---

## Executive Summary

The Vega program currently designates the Avery Dennison M8 as the sole recommended RFID tag for general merchandise (non-F&B). This single-source dependency creates supply chain risk that has already materialized: M8 availability has been constrained by tariffs, limited Avery Dennison international distribution infrastructure, and production strain as Vega scales into the UK and beyond.

The Starport M730 (Tageos241) is a proven alternative. It was first used in production at NA-AA-90 (Laufey at Crypto Arena, 09/26-09/27) where it enabled the sale of 1,319 additional items that would have otherwise gone untagged due to M8 supply shortfall. Combined with M8 tags, the event achieved 40.8 IPK and 7.7 customer-facing EPK. The tag demonstrated strong adhesive properties, zero detachment across ~1,900 applied tags, and required only a minor print alignment modification from AEG via Amazon Print Solution.

Adopting the M730 as an official tag type provides supply chain resilience, cost reduction for high-volume and F&B use cases, faster on-site application, and a blueprint for multi-supplier RFID interoperability as Vega scales globally.

---

## Advantages (Pros)

### 1. Supply Chain Resilience
- Eliminates single-source dependency on Avery Dennison for general merchandise tags
- M8 availability has been limited by tariffs and constrained international distribution — UK deployments have further complicated sourcing given the scarcity of AD warehouse locations
- The M730 provides a second sourcing path, ensuring Vega and its customers are not bottlenecked by one supplier
- At NA-AA-90, the M730 was available on-site (via Rank & Rally's existing inventory) when M8 supply ran short — without it, 1,319 items (~45% of total sales) would not have been tagged

### 2. Lower Unit Cost for F&B and High-Volume Merchandise
- StarportM730/Tageos tags cost $0.04/tag vs. $0.07/tag for M8 (43% savings per unit)
- At scale (22,000 tags per event with 10% buffer), all-Tageos material cost is $1,070.41 vs. $1,730.41 for all-M8 — a $660 savings per event
- Annual savings at 36 events: $38,534.76 (all Tageos) vs. $62,294.76 (all M8) — $23,760 annual material savings
- The M730 is already positioned in the contractor tagging program as the recommended tag for Bling 1/2/3 and Flag Tag 4 form factors used in F&B and high-volume merch

### 3. Faster On-Site Application (Direct-to-Garment)
- UK operations identified a requirement for tags applicable directly to clothing to reduce tagging overhead
- Traditional M8 hang-tag application: ~19 sec/item; M730 adhesive direct application: ~10 sec/item — a 47% reduction in tagging time per garment
- SOP feedback from NA-AA-90 (Jose Cano): "The application was much quicker and the ease of application was also better. The print-ability of the Starport tags is a bit easier due to the fact that you do not have to tear tags. So the time to tag items is a lot faster."
- M8 stickers require finer touch with a tag gun; M730 adhesive application is simpler and faster for all experience levels

### 4. Superior Adhesion on Clothing
- At NA-AA-90, ~1,900 Starport tags were applied on-site with zero detachments — none found on the floor during cleanup
- Tags remained securely attached through repeated folding by associates and customer try-ons
- "The M8 tag doesn't stick to most clothes as well as the Starport tag. When applied to t-shirts and hoodies, the M8 adhesive tends to peel off quickly. The Starport tag sticks well to clothes, even after a few test runs." — Jose Cano, SOP feedback
- Rank & Rally applies M730 tags directly behind shirt collar tags for their internal inventory — a placement that is less obvious than M8 and may reduce shrink

### 5. Concealed Form Factor
- Smaller antenna size (42x16mm) allows placement behind collar tags or in less visible locations
- SOP feedback: "Some customers might like that the Starport is more concealed. It would give more of a 'wow' factor when walking through the gates."
- Less visible tagging reduces customer perception of surveillance and improves the shopping experience

### 6. Customer Ecosystem Compatibility
- Rank & Rally already uses M730 tags for their internal inventory planning — they apply them at the warehouse and remove them after scanning
- Adopting the M730 allows Vega to support customers who already have Starport/Tageos tags in their RFID ecosystem, eliminating the redundant process of removing existing tags and replacing them with M8
- This positions Vega for multi-supplier interoperability as more customers bring existing RFID infrastructure

### 7. Proven Production Compatibility
- Lab testing was completed prior to the NA-AA-90 event
- Required only a slight modification to print alignment from AEG using Amazon Print Solution
- ML baseline has been established from production shopping data at NA-AA-90
- Starport exploratory eval and ML baseline work are complete

---

## Disadvantages (Cons)

### 1. Higher Unit Cost for Direct Apparel Comparison
- When compared specifically as an apparel sticker replacement for M8, the M730 costs approximately $0.18/tag vs. $0.08/tag for M8 — more than double the per-unit cost
- Note: The $0.04/tag cost referenced in the contractor tagging program applies to the Bling/Flag Tag form factors used for F&B and high-volume merch. The direct apparel sticker form factor carries the higher $0.18 price point
- This cost premium must be weighed against the operational savings from faster application time and reduced re-tagging

### 2. Smaller Font Size
- SOP feedback noted the font size on M730 tags "might be a bit small"
- This could impact readability for associates during manual inventory processes or tag verification
- May require print template optimization to maximize legibility within the smaller tag footprint

### 3. RF Performance Detuning Near Human Body
- Sensitivity detuning of 5-10dB worse than Bainbridge tag when interacting with the human body, due to longer antenna traces
- Standalone sensitivity is decent at approximately -15dBm with 42x16mm antenna — only 2-3dB worse than Bainbridge
- Overall tag performance is similar to Gen1 tag AD262
- This detuning is a known characteristic and was accounted for in the ML baseline built from NA-AA-90 production data

### 4. Smaller ML Baseline Sample Size
- NA-AA-90 production data: 7,019 total Starport tags vs. 28,359 M8 tags used for model inference
- While initial performance metrics are promising (IPK: 69.8 Starport vs. 42.6 M8; EPK: 12.4 Starport vs. 7.3 M8), the smaller sample size means the baseline needs further validation across additional events and store configurations
- Continued data collection at future deployments will strengthen the ML model for Starport-specific inference

### 5. Limited to Regular Merchandise
- The M730 is rated for regular merchandise only — not suitable for metal or liquid items (same as M8 for non-F&B)
- F&B items require dedicated tag types (Midas Flag-Tags or Bling variants); the M730 does not replace those

### 6. Less Versatile Than M8 for Customer Preference
- The M8 offers two application options (sticker + hang-tag), giving customers flexibility in how they tag merchandise
- The M730 is adhesive-only, which some customers may perceive as limiting
- "The versatility of the M8 tag is beneficial that gives the customer 2 options to apply the tag how they desire to a given product. It also looks more like a 'traditional' price tag." — Jose Cano, SOP feedback

### 7. Risks Section Incomplete for Accelerated Testing
- The original evaluation doc flagged a risks section for labops to complete regarding accelerated testing timelines — this remains empty
- Before full-scale rollout, labops should document any risks associated with accelerated adoption timelines so customers are informed

---

## Production Validation Summary

| Metric | M8 | Starport M730 |
|---|---|---|
| Total tags for model inference | 28,359 | 7,019 |
| Target tags | 2,068 | 888 |
| Stray tags | 26,291 | 6,131 |
| Target tags inquiries | 30 | 16 |
| Stray tags inquiries | 58 | 46 |
| Target tags error | 4 | 3 |
| Stray tags errors | 11 | 8 |
| Target tags IPK | 14.5 | 18.0 |
| Stray tags IPK | 28.0 | 51.8 |
| Target tags EPK | 1.9 | 3.4 |
| Stray tags EPK | 5.3 | 9.0 |
| IPK | 42.6 | 69.8 |
| EPK | 7.3 | 12.4 |

*Data from NA-AA-90 (Laufey at Crypto Arena, 09/26-09/27). Starport tags applied to neck area behind shirt tag per Rank & Rally warehouse practice.*

---

## Cost Comparison

### Per-Tag Unit Cost by Use Case

| Tag Type | Unit Cost | Primary Use Case |
|---|---|---|
| M8/Elevate (sticker + hang-tag) | $0.07 | Standard apparel |
| StarportM730/Tageos (Bling 1/2/3, Flag Tag 4) | $0.04 | F&B and high-volume merch |
| StarportM730 (direct apparel sticker) | $0.18 | Direct-to-garment apparel |
| Midas Flag-Tags | $0.20 | F&B primary; fastest application |

### Per-Event Material Cost (22,000 tags with 10% buffer)

| Scenario | Tag Cost | Ink/Ribbon | Total Materials |
|---|---|---|---|
| All M8/Elevate ($0.07) | $1,540 | $190.41 | $1,730.41 |
| All StarportM730/Tageos ($0.04) | $880 | $190.41 | $1,070.41 |
| All Midas Flag-Tag ($0.20) | $4,400 | $190.41 | $4,590.41 |
| Blended (50% M8 / 25% Midas / 25% Tageos) | $2,090 | $190.41 | $2,280.41 |

### Annual Material Cost (36 events)

| Scenario | Annual Tag Cost | Annual Ink | Annual Total |
|---|---|---|---|
| All M8/Elevate ($0.07) | $55,440 | $6,854.76 | $62,294.76 |
| All StarportM730/Tageos ($0.04) | $31,680 | $6,854.76 | $38,534.76 |
| All Midas Flag-Tag ($0.20) | $158,400 | $6,854.76 | $165,254.76 |
| Blended (50% M8 / 25% Midas / 25% Tageos) | $75,240 | $6,854.76 | $82,094.76 |

---

## Application Time Comparison

| Method | Time per Item | Notes |
|---|---|---|
| M8 Hang-Tag | ~19 sec | Requires tag gun, hole alignment |
| M8 Sticker (expert) | 11-12 sec | Serrated edges, 2-piece backing |
| M8 Sticker (new associate) | 22-34 sec | Finer touch required |
| Starport M730 direct adhesive | ~10 sec | Peel and apply; no tearing or gun |
| Efficiency gain (vs. hang-tag) | ~47% reduction | |

---

## Recommendation

Adopt the Starport M730 (Tageos241) as an officially supported tag type within the Vega program, offered to customers alongside the Avery Dennison M8. Specifically:

1. **F&B and high-volume merch (Bling/Flag Tag form factors at $0.04/tag):** Recommend as the default tag for these use cases — lower cost than M8 with comparable or faster application times.

2. **Direct-to-garment apparel ($0.18/tag):** Offer as an alternative to M8 for customers who prioritize application speed, adhesion quality, or concealed placement. The unit cost premium is offset by ~47% faster application and superior adhesion on clothing.

3. **Customers with existing Starport/Tageos ecosystems:** Offer as the primary tag to eliminate redundant re-tagging workflows (e.g., Rank & Rally currently removes their Starport tags and replaces with M8 for Vega — this step becomes unnecessary).

4. **Supply chain contingency:** Maintain as a qualified backup for M8 supply disruptions, ensuring no customer launch is delayed due to single-source tag availability constraints.

### Before Full Rollout
- Labops to complete the accelerated testing risks section
- Continue ML baseline data collection across additional events to strengthen Starport-specific model inference
- Validate print template optimization for font legibility on the smaller tag footprint
- Confirm AEG print alignment settings are documented and repeatable for all printer configurations

---

## Appendix

### A: RF Performance Notes
- Standalone sensitivity: approximately -15dBm with 42x16mm antenna size
- No obvious performance degradation — only slightly (2-3dB) worse than Bainbridge
- Human body interaction: sensitivity detuning 5-10dB worse than Bainbridge due to longer antenna traces
- Overall performance similar to Gen1 tag AD262
- Rated for regular merchandise only (no metal or liquid); not for F&B

### B: First Production Use — NA-AA-90 (September 2025)
Amazon pre-printed 2,933 M8 tags for the NA-AA-90 events based on Rank and Rally estimates. The two events sold 4,252 items — 1,319 more than estimated (45% variance). Rank and Rally had excess Starport tags on-hand from their EXO solution (competitor RFID self-checkout). Lab testing had been completed previously, permitting use with only a slight print alignment modification from AEG via Amazon Print Solution. Starport and M8 tags combined for 40.8 IPK and 7.7 customer-facing EPK.

Rank and Rally demonstrated direct application of Starport tags behind shirt collar tags. Despite initial adhesion concerns, no loose tags were found on the ground during cleanup. The placement was less obvious than M8 tags, which may reduce shrink.

### C: Cycle Counting Compatibility
The M730 uses standard EPC encoding (UPC → TID → EPC mapping) and is compatible with the RFID cycle counting pilot framework. Tagged items follow the same lifecycle: On Product → Induct → Inventory Check → State Change / Move / Bridge Sold → Retire. No modifications to the cycle counting workflow are required to support M730 tags.
