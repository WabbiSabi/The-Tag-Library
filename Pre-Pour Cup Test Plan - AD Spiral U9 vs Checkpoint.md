# Pre-Pour Cup RFID Tag Comparison — Test Plan
### AD Spiral U9 vs Checkpoint vs [Tag 3 — TBD]

---

## High-Level Test Description

We have been provided three viable tag-types for the pre-pour program. Spiral U9 had been previously evaluated with just the tags applied via tape to the bottom of plastic containers resulting in lower expectations for the viability of the product. However, final product samples were finally provided with much better read rates and have been re-added to the pre-pour program for end-to-end comparison and business evaluation.

This test plan provides a structured side-by-side evaluation of all three tag options across readability, durability, operationalization, and cost — using the Vega Gen 2.1 lane in production-representative conditions. Results will inform the tag selection recommendation for the pre-pour beverage program.

---

## Objective

Evaluate and compare three RFID-enabled cup tagging solutions for pre-poured beverage use cases. Testing focuses on the four criteria identified in the Pre-Poured Beverages Program doc: tag readability, durability, cost/aesthetics, and operationalization — grounded in failure modes observed at F1 COTA, PGA-AMEX, and LSU.

---

## Tags Under Test

| Attribute | AD Spiral U9 | Checkpoint | Tag 3 — TBD |
|---|---|---|---|
| Manufacturer | Avery Dennison | Checkpoint Systems | TBD |
| Form Factor | Cup-integrated (final product sample) | TBD — confirm | TBD — confirm |
| Previous Eval | Yes — tape-applied to cup bottom; poor read rates. Re-evaluated with final product samples showing significantly improved performance. | TBD | TBD |
| Estimated Unit Cost | $ _____ | $ _____ | $ _____ |
| Cup Compatibility | TBD | TBD | TBD |
| Min. Separation from Liquid | TBD (industry standard ~4mm) | TBD | TBD |
| Spec Sheet on File | ☐ | ☐ | ☐ |

> **Pre-test action:** Obtain spec sheets for all three tags. Confirm antenna design, recommended read distance, and any manufacturer-stated liquid/metal performance ratings. For Spiral U9, document what changed between the original tape-applied eval and the final product sample that improved read rates.

---

## Test Environment

| Parameter | Detail |
|---|---|
| Reader Hardware | Vega Gen 2.1 lane (production config) |
| Antenna Config | Standard gate antenna layout per current deployment |
| Cup Types | Standard 16oz plastic pint cup (UK football standard), 12oz plastic cup (US concession standard) |
| Liquid | Water (baseline), Beer (target use case) |
| Temperature States | Ambient (~20°C), Chilled (~4°C, simulating pre-pour fridge storage), Condensation-active (pulled from fridge, 10 min ambient exposure) |
| Control | M8 sticker on dry goods item (known-good baseline for read rate comparison) |

---

## Test Matrix

### 1. Readability — Can the gate see it?

The core challenge per the Pre-Poured Beverages doc: RF energy is absorbed by liquids and reflected by metals. These tests validate whether each tag maintains readability under real-world pre-pour conditions. For Spiral U9 specifically, this section validates whether the final product samples deliver on the improved read rates observed vs. the original tape-applied evaluation.

| # | Test | Procedure | Pass Criteria | Notes |
|---|---|---|---|---|
| 1.1 | Static read — empty cup | Place tagged empty cup on lane shelf. Record read rate across 10 passes. | ≥95% read rate | Baseline — isolates tag performance from liquid interference |
| 1.2 | Static read — filled cup (ambient) | Fill cup with water/beer at room temp. 10 passes. | ≥90% read rate | Primary readability gate |
| 1.3 | Static read — filled cup (chilled) | Fill cup with chilled liquid (~4°C). 10 passes. | ≥90% read rate | Simulates pre-pour fridge pull |
| 1.4 | Static read — condensation active | Pull chilled filled cup from fridge, let sit 10 min in ambient. 10 passes. | ≥90% read rate | Condensation was the #1 adhesion/read failure at F1 and PGA |
| 1.5 | Hand-carry read | Shopper holds filled cup by body and walks through gate at normal pace. 10 trials per tag. | ≥85% read rate | Human body detuning — ref: Starport M730 doc noted 5-10dB detuning near body |
| 1.6 | Multi-item cart | 1 tagged cup + 2 other tagged items (merch). Walk through gate. 10 trials. | Cup detected in ≥90% of trials | Validates cup tag doesn't get lost in multi-item read environment |
| 1.7 | Stacked cups (2-high) | Two filled tagged cups held together. Walk through gate. 10 trials. | Both cups detected ≥85% of trials | UK pre-pour scenario: customers buy 2 pints |
| 1.8 | Metal proximity | Tagged cup placed next to/on metal surface (counter, fridge shelf). 5 reads. | Confirm read or document failure | Metal reflection is called out as a primary challenge in the beverages doc |

### 2. Durability — Does it survive the event?

Pre-pour cups sit in fridges, get handled by associates, carried by customers, and may be in play for hours. Tags must survive the full lifecycle.

| # | Test | Procedure | Pass Criteria | Notes |
|---|---|---|---|---|
| 2.1 | Fridge soak — 1 hour | Tag cup, fill, place in fridge (4°C) for 1 hour. Remove, attempt read. | Tag reads successfully; no visible delamination | Simulates pre-pour staging |
| 2.2 | Fridge soak — 4 hours | Same as above, 4 hours. | Tag reads successfully; adhesive intact | Extended pre-pour window for high-volume events |
| 2.3 | Condensation + handling | After fridge soak, handle cup 10x (pick up, set down, pass between hands). Attempt read. | Tag reads; tag has not shifted or peeled | F1 learning: "When the adhesive gets wet, whether submerged or not, it's done for" |
| 2.4 | Wet submersion (accidental) | Submerge tagged portion of cup in 1cm of water for 30 sec (simulating spill/tub ice). Attempt read. | Document read success/failure and adhesive state | F1 used tubs; PGA had tub-related tag failures |
| 2.5 | Drop test | Drop filled tagged cup from counter height (~1m) onto hard surface. 5 trials. Check tag integrity and read. | Tag remains attached and readable in ≥4/5 trials | Concession environments are not gentle |
| 2.6 | Tamper resistance | Attempt to peel/remove tag by hand. Rate difficulty 1-5. | Document ease of removal | Beverages doc calls out tamper resistance as a requirement |

### 3. Operationalization — Can associates actually do this?

Tagging time studies show that tag type selection directly impacts labor cost. Pre-pour is a speed game — UK halftime windows are ~15 min.

| # | Test | Procedure | Pass Criteria | Notes |
|---|---|---|---|---|
| 3.1 | Application time — expert | Experienced tagger applies tag to 10 cups. Record avg time per cup. | Target: ≤5 sec/cup | Midas Flag-Tag baseline is 4-5 sec/item for experts |
| 3.2 | Application time — new associate | Untrained person applies tag to 10 cups after a 1-min verbal SOP. Record avg time. | Target: ≤8 sec/cup | New associate flag-tag baseline is 6-7 sec |
| 3.3 | Application consistency | Inspect 20 tagged cups for placement accuracy. Photo document. | ≥90% correctly placed per SOP | PGA showed associates placing tags in wrong positions on cans |
| 3.4 | Batch tagging workflow | Tag 50 cups in sequence (simulating pre-pour staging). Record total time and any workflow friction. | Document throughput rate and pain points | "Sales velocity is the highest priority" per beverages doc |
| 3.5 | Tag-to-cup fit | Assess physical fit: Does the tag sit flush? Does it interfere with drinking? Does it look acceptable? | Subjective rating 1-5 + photos | Beverages doc flags aesthetics as a customer expectation |
| 3.6 | Pre-tagged cup stacking | Can tagged cups be stacked for storage/transport without tag damage or interference? 10 cups stacked. | Tags undamaged after unstacking; read rate maintained | Pre-pour ops may require stacking cups before filling |

### 4. Cost & Aesthetics

| # | Evaluation | AD Spiral U9 | Checkpoint | Tag 3 — TBD |
|---|---|---|---|---|
| 4.1 | Unit cost per tag | $ _____ | $ _____ | $ _____ |
| 4.2 | Unit cost per cup (if integrated) | $ _____ | $ _____ | $ _____ |
| 4.3 | Delta vs. standard disposable cup ($0.007-$0.0125 ref) | $ _____ | $ _____ | $ _____ |
| 4.4 | Visual impact on cup (photo) | | | |
| 4.5 | Customer-facing acceptability (1-5 rating from 3+ people) | | | |
| 4.6 | Compatibility with existing cup suppliers | Y / N / TBD | Y / N / TBD | Y / N / TBD |
| 4.7 | Manufacturing scalability (can supplier meet volume?) | TBD | TBD | TBD |

---

## Scoring Summary

| Category | Weight | AD Spiral U9 | Checkpoint | Tag 3 — TBD |
|---|---|---|---|---|
| Readability (Tests 1.1–1.8) | 40% | /10 | /10 | /10 |
| Durability (Tests 2.1–2.6) | 25% | /10 | /10 | /10 |
| Operationalization (Tests 3.1–3.6) | 20% | /10 | /10 | /10 |
| Cost & Aesthetics (4.1–4.7) | 15% | /10 | /10 | /10 |
| **Weighted Total** | **100%** | **/10** | **/10** | **/10** |

---

## Logistics

| Item | Detail |
|---|---|
| Test Location | Gamma Lab / TBD |
| Cups Needed | 50x per cup size, per tag type (300 total minimum for 3 tags) |
| Liquid | 2x cases water, 1x case beer (or equivalent) |
| Fridge Access | Required — standard beverage fridge |
| Personnel | 1x test lead, 1x "new associate" volunteer for timing tests |
| Estimated Duration | 1 full day (5-7 hours active testing + documentation) |
| Equipment | Vega lane (or handheld RFID reader if lane unavailable), stopwatch, camera, thermometer |

---

## Open Questions

- [ ] Confirm third tag type — manufacturer, form factor, and sample availability
- [ ] For Spiral U9: document what specifically changed between the tape-applied eval and the final product sample (inlay redesign? cup integration method? spacer/separation improvement?)
- [ ] Confirm tag integration method for each option — embedded in cup wall, applied as sticker, or attached via sleeve/band?
- [ ] What is the minimum liquid separation each tag requires for reliable reads?
- [ ] Are reusable cup scenarios in scope? (Beverages doc references UK/EU reusable container companies piloting with McDonald's and Starbucks)
- [ ] Does the customer (venue/concessionaire) have a cup supplier preference that constrains options?
- [ ] What is the target price point per cup that makes this viable at scale?
- [ ] Is there a minimum order quantity or lead time constraint from any of the three suppliers?
