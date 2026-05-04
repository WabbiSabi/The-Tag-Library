# Vega RFID Operations — Gap Analysis for New Customer Template

## Purpose
This analysis identifies operational gaps, risks, and scheduling considerations across all documented Vega RFID launch processes. The goal is to inform a repeatable template for onboarding new customers that avoids the failure modes observed in pilot events (PGA-AMEX, O2, Camp Flog Gnaw, F1 COTA, Laufey, Zach Bryan, LSU, etc.).

---

## 1. GAPS IDENTIFIED

### 1.1 Pre-Engagement / Intake Gaps

| Gap | Evidence | Template Requirement |
|-----|----------|---------------------|
| No standardized catalog intake timeline | Camp Flog Gnaw: no UPCs provided; F1 COTA: proactive UPC creation required; PGA-AMEX: ~200% tag volume variance | Catalog freeze date must be contractually defined: +7 days for Tier 2/3, day-of flexibility for Tier 1 only |
| Merchant tag volume estimates are unreliable | PGA-AMEX: 7,000 estimated → ~17,000 actual; Laufey: 2,933 → 4,252 (45% variance) | Template must include a volume estimation multiplier (2x-3x merchant estimate) and mandatory 10% blank buffer stock |
| No formal MerchOps feasibility assessment process | Tagging feasibility is described in strategy docs but no standardized intake form or SLA exists | Create a MerchOps intake form with mandatory fields: item materials, packaging types, form factors, F&B presence, bespoke tagging flags |
| BD-to-MerchOps handoff is informal | Workflow docs describe parallel BD/MerchOps tracks but no documented SLA for when MerchOps receives intake data | Define SLA: MerchOps receives intake within 48 hours of BD discovery kickoff |

### 1.2 Site Survey & Logistics Gaps

| Gap | Evidence | Template Requirement |
|-----|----------|---------------------|
| No pre-launch site information package | PGA pilot: vendor arrived with no parking info, POC phone went to voicemail, no badging instructions | Standardized pre-launch checklist: POC contact + backup, parking, badging, entry gate protocols, site photos, start time confirmation |
| BOH space not assessed before tier classification | O2: BOH shared with cocktail tent, wires under their entrance; F1 COTA: arrived blind with no understanding of setup; PGA-AMEX: hot foods cooked next to beverage pallets | Site survey must include BOH space assessment with photos BEFORE tier classification decision |
| Infrastructure details not communicated to vendors | PGA: both stores on generators, 41-min power loss with no backup protocol communicated; power didn't arrive until 18 min after site opening | Template must require infrastructure disclosure: generator vs. grid, backup power protocols, POC for power issues |
| No store design optimization mechanism | Every pop-up to date has had suboptimal lane count; NA-AA-90 was the only store that didn't have enough lanes; others were over-provisioned | Create store design recommendation tool based on venue size, expected throughput, and shopper flow patterns |
| Shipping logistics are ad hoc and expensive | Sept 2025: $12,000+ in shipping across 4 stores; missed pickups, weekend premium charges, crate damage after 3-4 uses | Formalize shipping SOP with carrier relationships, guaranteed date pricing, crate condition tracking, and weekend/after-hours protocols |

### 1.3 Tagging Operations Gaps

| Gap | Evidence | Template Requirement |
|-----|----------|---------------------|
| No digital compliance checklist exists | Described as MVP in multiple docs but not yet built | Build MVP: photo upload at 5 checkpoints, pre-launch EPC scan, manual scoring rubric |
| F&B tags lack human-readable identification | Tagging Compliance doc: "Tags difficult to identify without titles"; F1 COTA: vendor using same sticker for different but similar products | Tag redesign to include titles or color-coded category identifiers; interim: printed reference sheets shipped with every F&B tag order |
| Tag adhesion failures on specific materials are not systematically tracked | F1: Smartwater tags fell off (condensation); chips with ridged tops; PGA: cookies on wax paper incompatible with M8; O2: best-seller had 6-10 tags fall off/day | Create material-tag compatibility matrix; include in site survey as mandatory validation step |
| Associate training is not scalable | PGA: QR-based training rejected on-site; Camp Flog Gnaw: language barriers required telephone-style SOP translation; LSU: rotating volunteers with high training burden | Develop 5-minute visual-first SOPs per tag type; vendor training video; tag application quick-guides (photo-based, 1-page) shipped with every order |
| EPC scan capture is inconsistently performed | PGA-AMEX: beginning-of-day scan missed "due to supporting two sites"; O2: untagged boxes in BOH not counted | Digital checklist must enforce EPC scan as mandatory checkpoint with photo proof; compliance scoring penalizes missing scans |
| No stray tag management protocol | F1: third-party RFID tags triggering gate reads; PGA: discarded tags on ground near gates; O2: 6-10 tags on floor day one | SOP for stray tag sweeps at open/close; gate proximity management (trash placement, product staging distance); CS team SOP for non-Amazon RFID reads |

### 1.4 Technology & Tooling Gaps

| Gap | Evidence | Template Requirement |
|-----|----------|---------------------|
| 3P vendors lack system access for independent operations | PGA pilot: no Mycroft camera access, TKS fields grayed out, TC device manager alias unresolved | System access provisioning (Mycroft, TKS full visibility, TC device manager) must be completed BEFORE vendor independence |
| TKS workflows lack embedded troubleshooting | PGA: antenna validation failed multiple times with no retry protocol; gateway connection diagnostics not documented; tamper errors not explained | Add decision trees for: antenna validation, gateway connections, tamper errors, receipt validation, crate management |
| Print template management is a single point of failure | PGA: "F1 TEMP" print option created by engineer, disappeared next morning, 3+ hours no on-call response | Print template changes must be self-service or have documented backup procedures with defined SLAs |
| No automated compliance scoring | Currently manual calculation; described as target for Q3 2026 | Interim: spreadsheet-based scoring template; target: automated digital tooling |
| Supply chain approval bottleneck for tag resupply | O2: hotshot order blocked for hours pending managerial approval; "our entire supply chain needs an approval that only a couple of people can give" | Pre-authorized resupply thresholds; contractor can trigger orders below defined quantity without managerial approval |
| Cycle counting not yet operational | Pilot plan defined (R0 → P1 → P1.5) but not yet deployed; O2 and Camp Flog Gnaw both demonstrated need | Cycle counting must be scoped into every new 2026 launch per MBR direction |

### 1.5 Vendor Management Gaps

| Gap | Evidence | Template Requirement |
|-----|----------|---------------------|
| Single vendor dependency risk | Only Action Link and WIS International evaluated; no backup if both are unavailable | Maintain competitive dual-vendor model; Q2 2026 vendor pool expansion is critical |
| Vendor staffing lead times conflict with pop-up timelines | Action Link: 6-8 weeks notice required; pop-up events often confirmed with shorter lead times | Template must flag staffing lead time at intake; events with <6 week notice may need Tier 1 classification override |
| No formalized communication SLAs | PGA: unanswered vendor requests, 41-min hard block without acknowledgment, 4-17 min response variability | Define response SLAs: critical issues <5 min, technical questions <15 min, picture requests <10 min |
| Vendor quote structure not finalized for customer pass-through | Action Link $2,000 min management fee per project significantly impacts economics at scale ($72K across 36 events) | Negotiate bundled/retainer pricing; clarify which costs are Amazon-absorbed vs. customer pass-through |
| No vendor SLA for tagging compliance, EPC capture, or reporting | Described as Phase 4 target but not yet formalized | Interim: event-level compliance scoring with 24-hour report submission requirement |

### 1.6 Post-Event & Reporting Gaps

| Gap | Evidence | Template Requirement |
|-----|----------|---------------------|
| No standardized post-event reconciliation process | PGA-AMEX: customer "super dependent" on reports, raised SEV2 when unavailable; O2: shrink analysis required manual cross-referencing of wand scans, NM sales, and Brahmos data | Standardized post-event report template: EPC reconciliation, sales vs. tagged inventory, shrink analysis, compliance score |
| Receipt lookup doesn't explain mobile wallet to shoppers | Sept retro: EPC Receipt Lookup Website doesn't explain how to acquire credit card number for mobile wallets | Product fix needed; interim: associate training on mobile wallet receipt lookup |
| No formalized teardown/re-crating SOP for pop-ups | PGA: crates broken down due to space constraints but teardown crew differed from launch crew; crates showing wear after 3-4 uses | TKS must include crate storage decision capture at launch; push to teardown instructions; notify vendors of increased time if crates disassembled |
| Customer payment reconciliation is manual | MBR: using lab MID for 7 stores created manual reconciliation overhead across multiple dashboards | Fully Integrated payment model (tech ready 2/11) must be validated before new customer onboarding |

---

## 2. RISK REGISTER FOR NEW CUSTOMER TEMPLATE

### Critical Risks (High Likelihood, High Impact)

| # | Risk | Likelihood | Impact | Mitigation |
|---|------|-----------|--------|------------|
| R1 | Merchant provides incomplete/late catalog data | Very High | High — blocks pre-printing, causes on-site scramble | Contractual catalog freeze date; 10% blank buffer; Tier 1 fallback for non-compliant merchants |
| R2 | Tag volume estimates underproject by 45-200% | Very High | High — tag shortage forces POS fallback (O2 scenario) | Apply 2x-3x multiplier to merchant estimates; pre-authorized resupply path; blank buffer stock at every event |
| R3 | Associate/volunteer workforce is unreliable | High | High — compliance degradation, inconsistent SOP adherence | Tier 1 classification for volunteer-dependent events; vendor-owned tagging for critical events; simplified visual SOPs |
| R4 | F&B tag adhesion failure (condensation, ridged surfaces, hot food) | High | Medium — mistagged items, incorrect pricing, customer confusion | Material-specific SOPs; 3-hour chill time for pre-tagged beverages; tag type recommendation matrix per merchandise category |
| R5 | Power/infrastructure failure at pop-up venue | Medium | High — hard-blocks all operations | Pre-launch infrastructure disclosure; generator protocols in TKS; backup power POC escalation path |
| R6 | Vendor cannot staff within required lead time | Medium | High — launch delay | Dual-vendor model; flag lead time at intake; maintain Amazon fallback capacity for critical launches |
| R7 | System access gaps block vendor independence | High | Medium — creates blue badge dependency | Resolve Mycroft, TKS, TC device manager access before declaring vendor-independent operations |

### Moderate Risks

| # | Risk | Likelihood | Impact | Mitigation |
|---|------|-----------|--------|------------|
| R8 | Event postponement mid-deployment | Medium | Medium — re-mobilization costs, power/network reset | Vendor SOPs include postponement protocols; equipment securing checklist; schedule RFID-active days back-to-back |
| R9 | Stray tags / third-party RFID interference | Medium | Medium — false gate reads, phantom inventory | CS team SOP for non-Amazon RFID; gate proximity management; stray tag sweeps at open/close |
| R10 | Pre-printed tag fulfillment errors | Medium | High — unusable tags discovered on-site | QA spot-check ≥5% of every order; EPC scan validation before packaging; photo-based manifest confirmation |
| R11 | Crate damage from repeated pop-up use | High | Low-Medium — delays uncrating, increases costs | Track crate condition; 3rd-gen crate design in progress; budget for crate replacement every 4-5 uses |
| R12 | Single point of failure — Gamma lab for pre-printing | Low | High — all pre-print orders blocked | Printer fleet maintenance schedule; backup printers; Phase 4 evaluates regional satellite locations |
| R13 | Merchant reverts to POS during RFID outage and wastes tags | Medium | Medium — tag waste, operational confusion | Clear communication to merchants about gate status; tagging pause protocol during non-RFID periods |

---

## 3. LOGISTICAL SCHEDULING — CUSTOMER CONVERSATION FRAMEWORK

### Timeline: What Must Be Discussed and When

#### T-12 to T-10 Weeks (Intake & Discovery)
- BD submits intake to MerchOps (catalog, merch count, item types, packaging, sales data, logistics)
- BD submits SCOT intake to kick off IM workstream (NDA, contract, technical scoping)
- MerchOps begins catalog and technology evaluation
- Discuss with customer: **What is your merchandise mix? Do you have UPCs for all items? What percentage is F&B vs. apparel? Do you have existing RFID tags in your ecosystem?**
- Flag to customer: **Catalog data quality directly determines tagging accuracy and cost. Incomplete catalogs are the #1 cause of launch-day issues.**

#### T-8 to T-6 Weeks (Feasibility & Vendor Engagement)
- MerchOps outputs tagging feasibility assessment
- Tier classification determined (Tier 1/2/3)
- Service model selected (Model A: Full-Event / Model B: Launch-Day / Model C: Audit)
- Vendor engagement initiated (Action Link needs 6-8 weeks; WIS needs 7-14 day pre-visit)
- Discuss with customer: **Based on your inventory predictability and staffing model, here is our recommended service tier and vendor model. Here is the cost quote.**
- Flag to customer: **If you cannot commit to a final SKU list by T-7 days, you will be classified as Tier 1 (full on-site printing) which carries higher vendor labor costs.**

#### T-6 to T-4 Weeks (Pre-Print & BOM)
- Pre-print fulfillment initiated for Tier 2/3 events (catalog must be frozen at T-7 days)
- BOM shipment arranged (printer, ink, blank tags, hangtag accessories, hardware)
- Site survey scheduled (WIS: free visit 7-14 days before project)
- Discuss with customer: **We need confirmed site access details, BOH space photos, infrastructure details (power source, network), and your staffing plan for the event.**
- Flag to customer: **Missing hardware or late BOM arrival has caused launch delays. Confirm receiving dock access, POC availability, and storage space.**

#### T-3 to T-1 Weeks (Final Prep)
- Catalog freeze enforced for Tier 2/3 (any changes after this point reclassify to Tier 1)
- Pre-printed tags shipped with 10% blank buffer stock
- Tag application quick-guides and material-specific SOPs shipped with tag order
- Vendor receives SOPs and confirms staffing
- TKS workflow created by TDPM
- Discuss with customer: **Final catalog confirmation. Any changes from this point will require on-site printing and may increase costs. Confirm your associate staffing plan and training schedule.**
- Flag to customer: **Your associates will need to be trained on tagging SOPs. We provide visual guides and can do a 15-minute virtual walkthrough. Associate training adequacy directly impacts your non-payment loss rate.**

#### T-0 (Launch Day)
- Vendor on-site for uncrating, installation, and tagging operations
- Virtual bring-up and validation (TKS-guided)
- Opening EPC scan (mandatory)
- Discuss with customer: **Who is your on-site POC? What is the backup contact? What are your store hours? When does merchandise arrive?**
- Flag to customer: **EPC scans at store open and close are mandatory for reconciliation against your sales reports. Missing scans create blind spots in inventory tracking.**

#### T+1 to T+3 Days (During Event — Pop-Ups)
- Daily EPC scans (open/close/replenishment)
- Tagging compliance monitoring
- Vendor or associate handles replenishment tagging (per service model)
- Discuss with customer: **How is replenishment happening? At what intervals? Who is responsible for tagging restocked items?**
- Flag to customer: **Untagged items entering the store are undetectable by gates and will result in shrink. At O2, this caused ~£10k in losses (6.6% of sales).**

#### T+Event Close (Post-Event)
- Final EPC scan capture
- Digital compliance checklist completion with photo documentation
- Post-event report submission within 24 hours
- Teardown and re-crating (pop-ups)
- Discuss with customer: **We will provide a reconciliation report comparing EPC data against your sales records. This data informs inventory accuracy, shrink analysis, and future event planning.**
- Flag to customer: **For pop-ups requiring teardown, confirm dock access and pickup timing. Weekend/after-hours shipping carries premium charges.**

---

## 4. KEY METRICS TO SET EXPECTATIONS WITH NEW CUSTOMERS

| Metric | Target | Context |
|--------|--------|---------|
| Non-payment loss rate | < 2% (goal); post-DPA average < 1% | Pre-DPA stores drove 2025 rates above 2%; DPA + partial capture now achieving 0.3% |
| Tagging compliance rate | ≥ 95% | Vendor-owned tagging at Tier 1 events; associate-applied at Tier 2/3 with oversight |
| Tag application time (associate) | ≤ 15 sec/item | Trained associates; untrained can be 25-34 sec/item for M8 stickers |
| Tag application time (vendor tech) | ≤ 8 sec/item | Midas Flag-Tags and Bling 1/3 at 3-6 sec/item are fastest |
| EPC scan capture | 100% (open/close per event day) | Missing scans block reconciliation; PGA-AMEX SEV2 raised when reports unavailable |
| Pre-print fulfillment accuracy | ≥ 98% | Correct UPC-to-tag mapping; no VOID prints shipped |
| Store setup time (3P TD) | 8 hours per 2-3 lane store | Target 90% completion rate; current pilot data from PGA and KSC |
| Receipt latency P90 | < 120 seconds (HC carts) | Post-operational fixes trending at ~105 seconds |
| Lane utilization (pop-up) | Varies by venue | NA-AA-90 hit 78% (under-provisioned); most others 8-28% (over-provisioned) |

---

## 5. WHAT'S NOT YET BUILT (Blockers for Template Finalization)

1. **Digital compliance checklist** — MVP not yet deployed; manual scoring only
2. **Automated compliance scoring** — target Q3 2026
3. **Vendor training video** — not yet produced
4. **F&B tag redesign** — tags still lack human-readable titles
5. **Self-guided customer deployment tool** — BRD forthcoming; pilot Q2 2026, GA Q3 2026
6. **Cycle counting integration** — pilot plan defined but not yet operational
7. **Fully Integrated payment model** — tech ready 2/11/2026; not yet validated at scale
8. **Store design recommendation tool** — no mechanism exists to optimize lane count per venue
9. **Formalized shipping SOP** — carrier relationships and guaranteed-date pricing not established
10. **Pre-authorized supply chain resupply** — approval bottleneck not yet resolved
11. **Regional pre-print satellite locations** — Gamma lab is single point of failure; evaluation in Phase 4
12. **Vendor SLA contracts** — tagging compliance, EPC capture, and reporting SLAs not yet formalized

---

## 6. RECOMMENDED TEMPLATE STRUCTURE FOR NEW CUSTOMERS

A new customer onboarding template should include these sections as a minimum:

1. **Customer Profile** — Venue type (permanent/pop-up), merchandise mix (apparel/F&B/mixed), estimated SKU count, event duration, staffing model
2. **Tier Classification Worksheet** — Checklist-based scoring against Tier 1/2/3 criteria
3. **Catalog Intake Form** — Mandatory fields: UPC, title, price, tag type, quantity, packaging type, material notes
4. **Site Survey Checklist** — BOH space, power source, network, dock access, POC contacts, safety requirements
5. **Tagging Operations Plan** — Service model selection, vendor assignment, pre-print vs. on-site decision, tag type recommendation per category
6. **Cost Estimate Worksheet** — Vendor labor, materials (tags + ink), shipping, BOM, T&E
7. **Timeline & Milestone Tracker** — Mapped to the T-12 through T+Close framework above
8. **Risk Acknowledgment** — Customer signs off on catalog freeze requirements, staffing commitments, and infrastructure responsibilities
9. **Post-Event Reporting Template** — EPC reconciliation, compliance score, shrink analysis, lessons learned