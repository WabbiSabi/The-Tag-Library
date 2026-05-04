# HB Meeting — Agenda & Talking Points

*Perspective: Solutions Architect — Risks, Gaps, and Considerations for HB Onboarding*

---

## Meeting Goals

1. **Sync'd on Plans** — Establish regular comms cadence going forward
2. **HB Knows What to Do** — Tagging, cycle count, lane move/BU, escalation paths
3. **What Resources Are Needed?** — Tagging labor, store ops (replenishment), tech net staffing
4. **Inventory Tracking Reqs** — Define what HB needs to see and when
5. **Sales Reporting Reqs** — Reconciliation format, frequency, and data ownership
6. **RACI** — Clear ownership across JWO, HB, and any 3P vendors
7. **Store Design Constraints** — Lane count, BOH/FOH layout, fixture types
8. **FOH/BOH Ops Constraints** — Replenishment flow, returns handling, associate task allocation

---

## Agenda

### 1. Introductions

### 2. HB Reviews Existing Plan

#### Merch Logistics & Dates
- Sortation & distribution plans
- **SA Consideration:** Catalog freeze date must be contractually defined. At Camp Flog Gnaw, no UPCs were provided by the merchant — we had to create them in-house to unblock tagging. At PGA-AMEX, the actual tag volume was ~200% over the merchant's estimate (7,000 → ~17,000). Ask HB: *What is your catalog finalization timeline? Can you commit to a SKU freeze at T-7 days?*

#### Labor Pool / Plan
- Warehouse staffing
- At venue staffing
- **SA Risk:** Volunteer/part-time workforces have been unreliable across every pilot. At PGA-AMEX, teen volunteers had inconsistent SOP adherence and the customer faced an emergency at 20:00 when volunteers refused to work JWO tents due to lack of tips. At O2, the merchant said "tagging took too long, we will be doubling our staff." Ask HB: *What is your staffing model — paid associates or volunteers? What is your backup plan if staffing falls short on event day?*
- **SA Risk (Tips):** PGA-AMEX revealed that volunteer-driven models break down when there's no tipping mechanism. A paid associate had to be placed as a stopgap. Ask HB: *Does your ops model rely on tipped labor? If so, how does JWO's no-tip gate model affect your staffing pipeline?*

#### BOH Ops Plan
- **SA Consideration:** BOH space has been a recurring blind spot. At O2, BOH was shared with a cocktail tent and wiring ran under their entrance. At PGA-AMEX, hot foods were cooked directly next to beverage pallets, creating tag adhesion issues from heat/condensation. Ask HB: *Can you provide BOH layout photos and confirm dedicated space for tagging operations? Is there F&B prep happening in or near the tagging area?*

#### FOH Ops Plan
- **SA Consideration:** Every pop-up to date has had suboptimal lane provisioning — most were over-provisioned (8-28% utilization), one was under-provisioned (78%). At PGA-AMEX, the merchant moved FOH barriers mid-event for better throughput. Ask HB: *What is your expected peak throughput? What is your store layout flexibility on event day?*
- **SA Gap:** No store design recommendation tool exists yet. Lane count optimization is currently manual and based on SA judgment.

#### Interstore Ops + Logistics & Replenishment
- **SA Risk:** Replenishment tagging is where compliance breaks down. At O2, untagged boxes in BOH were never counted. At PGA-AMEX, the vendor wouldn't open every case (to preserve return eligibility), making pre-tagging impossible — printing became ad hoc. Ask HB: *How does restocking work? During event? Only at close? Who is responsible for tagging restocked items? Will vendors open all cases?*
- **SA Risk:** At O2, a day pause between RFID-active days caused the merchant to tag incorrectly overnight, leading to operational confusion. Lesson learned: RFID days should be back-to-back. Ask HB: *What is your event schedule? Are there any non-consecutive operating days?*

#### Inventory Tracking Reqs
- **SA Risk:** EPC scan capture has been inconsistently performed. At PGA-AMEX, a beginning-of-day scan was missed "due to supporting two sites." Missing scans block reconciliation entirely. Ask HB: *Who on your team will own daily EPC scans? Do you have a backup person?*
- **SA Consideration:** At PGA-AMEX, the customer raised a SEV2 because they couldn't see sales reports — they were "super dependent" on them for supply ordering. Ask HB: *What reporting cadence do you need? What decisions are you making based on this data?*

#### Sales Reporting Reqs
- **SA Gap:** Post-event reconciliation is currently manual — O2 required cross-referencing wand scans, NM sales details, and Brahmos data from AEG. Customer payment reconciliation uses a lab MID across multiple stores, creating overhead. Ask HB: *What does your current sales reporting look like? What format/system do you need data delivered in?*
- **SA Consideration:** Fully integrated payment model is tech-ready but not yet validated at scale. Set expectations with HB that reconciliation may require some manual steps initially.

---

### 3. RFID Gap Analysis

#### Tagging — Warehouse vs. On-site
- **SA Risk:** Tag location matters. At PGA-AMEX, all beverage inventory was pre-tagged incorrectly (top of cans instead of optimal position), causing elevated IPK/EPK rates. Thousands of misplaced tags with limited staffing to correct. At O2, the beanie tag had to be relocated mid-event from the manufacturer's tag to the brim because of missed reads. Ask HB: *Who is doing the tagging? Have they been trained? Can we do a tagging validation before go-live?*
- **SA Risk (EPC to wrong site):** If HB operates multiple locations (e.g., LA vs. Tampa), EPCs printed for one site could be inducted to the wrong site. At Camp Flog Gnaw, tags were printed in Gamma and hand-carried to a 3P warehouse in Compton — chain of custody was informal. Ask HB: *How many sites are you operating? What is your logistics flow for getting tagged inventory to the correct location?*

#### Shipping
- **SA Risk:** Shipping logistics have been ad hoc and expensive — $12,000+ across 4 stores in Sept 2025, with missed pickups, weekend premium charges, and crate damage after 3-4 uses. No formalized shipping SOP exists. Ask HB: *What are your receiving dock constraints? Weekend/after-hours availability? Who is the receiving POC?*

#### Bring Up (esp. networked lane — new assoc)
- **SA Risk:** At PGA-AMEX, power didn't arrive until 18 min after site opening. Both stores were on generators with no backup protocol communicated. A 41-min power loss occurred with no acknowledgment. At Camp Flog Gnaw, power and network were turned off mid-week during postponement, requiring full re-bring-up. Ask HB: *What is your power source (generator vs. grid)? What is the backup power protocol? Who is the POC for infrastructure issues?*
- **SA Gap:** TKS workflows lack embedded troubleshooting. Antenna validation, gateway connections, and tamper errors have no documented retry protocols.

#### BOH Ops — JWO vs. non-JWO
- **SA Consideration:** At PGA-AMEX, the tent manager (Julie) became the de facto POC for all operational needs, submitting ~11 tag requests daily based on real-time sales patterns. The actual JWO ops presence needed was more "guiding" than technical. Ask HB: *Who is your on-site ops lead? Do they understand the difference between JWO-managed processes and merchant-managed processes?*

#### FOH Ops — Replenishment, Returns, Assoc Tasks
- **SA Risk:** At O2, the merchant's exchange process was a simple 1:1 swap with no noting of what was swapped. Their inventory model tracked total revenue over item-level detail. This creates reconciliation blind spots. Ask HB: *What is your returns/exchange policy? Do you track at the item level or revenue level?*
- **SA Risk:** At O2, the "no trying-on" policy led to more exchanges/refunds. At PGA-AMEX, customers in queue backed up when POS was used as fallback during RFID outage. Ask HB: *What is your fitting/try-on policy? What is your fallback plan if gates go down?*
- **SA Consideration:** Associates removing RFID tags during POS fallback creates downstream issues — if gates come back online, untagged items on the floor are invisible. At O2, the merchant was told not to remove tags during POS mode, but this needs to be explicitly communicated. Ask HB: *If we fall back to POS, your associates must NOT remove RFID tags. Is that understood?*

---

## Current Agenda (Tour Planning)

### 1. General Tour Planning

### 2. Training Plan
- Crate load / unload
- Physical deployment
- Daily bring up
- Store ops (BOH / FOH)
- Assoc tasks (BOH / FOH)
- Shopper experience
- RFID tagging
- Cycle counting

**SA Gap:** Associate training is not scalable. At PGA-AMEX, QR-based training was rejected on-site. At Camp Flog Gnaw, language barriers required telephone-style SOP translation. Vendor training video does not yet exist. Current best practice is 5-minute visual-first SOPs per tag type, shipped with every order. Ask HB: *What is the primary language of your associates? What is your preferred training format? Can we schedule a 15-min virtual walkthrough before event day?*

**SA Consideration (Need SOPs):** SOPs are needed for uncrating, deployment, daily bring up, tagging, cycle counting, and sales reporting. These should be photo-based, 1-page quick-guides. The whiteboard flagged this as a dependency — confirm SOP delivery timeline with the team.

### 3. Opens

---

## Risks — Key Items to Raise with HB

| # | Risk | Evidence | Question for HB |
|---|------|----------|-----------------|
| 1 | **Tips / volunteer retention** | PGA-AMEX: emergency at 20:00, volunteers refused to work | What is your staffing model? Does it depend on tips? |
| 2 | **Tags in wrong location (EPC to wrong site)** | Camp Flog Gnaw: tags hand-carried across locations informally | How many sites? What is your logistics chain of custody? |
| 3 | **Escalation / resolution of tech/ops issues** | PGA-AMEX: 3+ hours no on-call response for print template; O2: supply chain approval blocked for hours | Who is HB's escalation POC? What is the expected response SLA? |
| 4 | **Tag volume underestimation** | PGA-AMEX: 200% variance; Laufey: 45% variance | Can we apply a 2-3x multiplier to your estimate? Will you pre-authorize resupply? |
| 5 | **Tag adhesion failure on specific materials** | O2: best-seller lost 6-10 tags/day; PGA: cookies on wax paper incompatible; condensation on beverages | What is your full merchandise material list? Any F&B, metal, condensation-prone items? |
| 6 | **Power/infrastructure failure** | PGA: 41-min power loss, generator-dependent; Camp Flog Gnaw: power cut mid-week | What is your power source and backup protocol? |
| 7 | **Merchant reverts to POS and wastes tags** | O2: merchant printed/tagged all day during gate downtime, burned through 2,400 tags | Clear protocol needed: when gates are down, tagging pauses. |

> **Staffing Note:** 6 Tech Net × 2 Days (3w VSL)

---

## Training (Need SOPs)

- Uncrating
- Deployment
- Daily bring up
- Tagging
- Cycle counting
- Sales reporting

**SA Note:** All SOPs should be visual-first, photo-based, 1-page max. Ship with every tag order. Include material-specific tagging guidance (sticker vs. hang-tag vs. flag-tag) based on the validated tag catalog for HB's merchandise mix.
