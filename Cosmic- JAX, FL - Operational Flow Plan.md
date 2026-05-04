# Cosmic Touring: Operational Flow Plan
### Solutions Engineering Recommendation — Based on JAX, FL (Game 1) Observations

---

## Executive Summary

The JAX Game 1 launch surfaced several recurring pain points around staffing deployment, physical layout, merchandise logistics, and system reliability. This plan restructures the event into phased operational windows with clear ownership, optimized labor allocation, and technical safeguards — designed to be repeatable across touring venues.

---

## Event Timeline & Phased Operations

### Phase 0 — Advance Setup (T-48h to T-5h)
| Window | Activity | Owner |
|---|---|---|
| T-48h | Trailers arrive on-site; begin unloading indoor-tent merchandise to nearest available BOH/basement storage | Logistics Lead |
| T-48h | Scout freight elevator access, map routes from BOH to every tent cluster (inside + outside). Document and photograph for crew briefing | Solutions Engineer |
| T-24h | Stage all POS hardware, printers, and laptops in BOH. Power on, charge, and run full connectivity test against Insight dashboard | Tech Lead |
| T-24h | Validate Shopify → Insight catalog sync. Confirm every active SKU resolves in Insight and prints a test tag. Flag discrepancies to RIOT immediately — do not wait until game day | Tech Lead |
| T-5h | Pre-position merchandise chests: outdoor tent stock staged at trailer tailgate, indoor tent stock staged in BOH closest to elevator/stair route | Logistics Lead |

**Key Change:** Catalog sync and printer validation happen the day before, not morning-of. This eliminates the #1 and #3 reported issues from JAX under time pressure.

---

### Phase 1 — Block Party Prep & Training (T-5h to T-4h / 10:00–14:00 equivalent)

| Window | Activity | Owner |
|---|---|---|
| T-5h | All ~30 associates arrive. Immediately split into three role-based training tracks (see Staffing Model below) — no one stands idle | Ops Manager |
| T-5h | Track 1 — POS Cashiers (10 associates): Gabe runs POS training with live transactions on test catalog | Gabe / Tech Lead |
| T-5h | Track 2 — Tent Leads & Restockers (10 associates): Walk the physical layout, learn restock pull points (trailer → outdoor, BOH → indoor) | Logistics Lead |
| T-5h | Track 3 — Roaming Sales / Cart Operators (6 associates): Briefed on bubble wand cart routes, Lights Out timing, upsell talking points | Ops Manager |
| T-5h | Track 4 — VIP Lounge (4 associates): Briefed on VIP layout, ~120 guest cap, curated selection | Ops Manager |
| T-4h | All tracks converge for 15-min venue walkthrough. Every associate sees the full map: tent locations, BOH, trailer, elevator routes, and emergency exits | Ops Manager |

**Key Change from JAX:** At JAX, 18 of 30 associates had no structured task during training hour. This model ensures 100% utilization from arrival.

---

### Phase 2 — Block Party Live (T-4h to T-0 / 15:00–19:00)

#### 2A. Layout Optimization

**Problem observed at JAX:** Tents placed directly facing ballpark entrance caused the merch queue to physically block stadium ingress, creating congestion and a poor first impression.

**Actual space:** 31' wide × 80' long, barricaded rectangle. Merch tents and ballpark entrance sit directly across from each other on the 31' width (center of the long sides), with the queue currently zigzagging between them — blocking ingress.

**The core problem:** With only 31' of width, a zigzag queue between the tents and the entrance eats the entire corridor. Customers trying to enter the ballpark have to fight through the merch line.

**Recommended layout — push tents to one end, queue runs lengthwise:**
```
    ◄──────────────────── 80' ────────────────────►

    ┌──────────────────────────────────────────────────────────────────────────┐
    │                                                                          │ ▲
    │   ┌────────┐ ┌────────┐ ┌────────┐ ┌────────┐                           │ │
    │   │ TENT 1 │ │ TENT 2 │ │ TENT 3 │ │ TENT 4 │     BALLPARK ENTRANCE    │ │
    │   │ 2xPOS  │ │ 2xPOS  │ │ 2xPOS  │ │ 2xPOS  │     ┌──────────────┐    │ │
    │   └───┬────┘ └───┬────┘ └───┬────┘ └───┬────┘     │              │    │ 31'
    │       │          │          │          │           │    DOORS     │    │ │
    │   ┌───┴──────────┴──────────┴──────────┴───┐      │              │    │ │
    │   │         QUEUE (single-file or           │      └──────────────┘    │ │
    │   │          2-wide, runs lengthwise)        │                          │ │
    │   │         ◄── flows toward tents ──        │      ▲ CLEAR LANE ▲     │ │
    │   └─────────────────────────────────────────┘      (min 10' wide)     │ ▼
    │                                                                          │
    └──────────────────────────────────────────────────────────────────────────┘
              ▲
              │
        ┌─────┴─────┐
        │  TRAILER   │
        │ (restock)  │
        └────────────┘
```

**What this changes:**
- Tents pushed to the far-left end of the 80' length, clustered side by side (4 tents × ~7' each = ~28', fits within 31' width)
- Queue forms in front of the tents and extends lengthwise down the 80' corridor — no longer zigzagging across the width
- Ballpark entrance sits on the opposite (right) side of the 31' width with a dedicated 10'+ clear lane that the queue never crosses
- Trailer parks at the near end behind the tents for direct restock access without crossing customer flow or the ingress lane
- Customers entering the ballpark walk the clear lane on the right side, passing the merch tents (visual exposure) but never getting tangled in the queue

**Why this works in 31' of width:**
- 4 tents side-by-side: ~28'
- Remaining ~3' on the tent side is buffer/associate workspace
- The 10' clear lane and queue lane share the 80' length, not the 31' width — so width pressure is relieved
- If 31' feels tight with tents + clear lane side by side, stagger tents into an L-shape at the corner to buy back a few feet

**Fallback if venue forces center placement:**
If the ballpark entrance truly cannot move and tents must stay centered across from it, then:
- Run the queue along one 80' wall only (no zigzag) using riot fence as a single-direction lane
- Keep the opposite 80' wall as the clear ingress path
- This still separates merch traffic from ballpark traffic, just with less queue capacity

#### 2B. Staffing Deployment — Block Party

| Role | Count | Responsibility |
|---|---|---|
| POS Cashier | 8 (2 per tent) | Ring sales. Speed is gated by POS — this is the bottleneck, not fulfillment |
| Tent Lead | 4 (1 per tent) | Manages display, answers product questions, keeps tent organized |
| Restockers | 3 | Pull from trailer → tents. Rotate every 45 min to stay fresh |
| Queue Manager | 1 | Directs foot traffic, keeps ingress lane clear, manages line if it builds |
| Floater | 2 | Break relief, handles edge cases, assists where volume spikes |
| **Total Outside** | **18** | |

**Key Change from JAX:** Reduced from 4 associates per tent to 3 (2 cashiers + 1 lead). Eliminated the dedicated "runner" role — in a 4-tent setup the space is too tight and POS speed is the actual constraint, not item retrieval. Freed-up headcount reallocated to queue management and restocking.

---

### Phase 3 — Block Party → Stadium Transition (T-0 to T+0:30 / 19:00–19:30)

This is the highest-risk window. Merchandise, hardware, and people all move simultaneously.

| Step | Action | Duration | Owner |
|---|---|---|---|
| 1 | Block Party tents stop accepting new customers in queue | T-0:15 | Queue Manager |
| 2 | Final transactions processed, POS terminals powered down and secured | 10 min | Cashiers |
| 3 | Remaining outdoor stock sorted into two streams: (A) items going to indoor tents, (B) items going to restock chests for next venue | 15 min | Restockers + Logistics Lead |
| 4 | Stream A moved via pre-mapped route to indoor tent clusters. Each bin labeled by tent destination BEFORE leaving the staging area | 15 min | Restockers |
| 5 | Stream B loaded into chests at trailer | Concurrent with Step 4 | Logistics Lead |
| 6 | Outdoor tents broken down or secured | 15 min | Tent Leads + Floaters |

**Key Change from JAX:** At JAX, all Block Party items were moved inside and "integrated" into venue merch with no labeling — creating mix-up risk across multiple floors with limited elevator access. Pre-labeling bins by destination tent before they leave staging eliminates cross-contamination.

**Elevator/Freight Constraint Mitigation:**
- Map every freight elevator and stairwell route during Phase 0. Assign specific routes to specific tent destinations.
- If freight elevator access is limited (as at JAX), pre-stage indoor tent stock from BOH during Phase 1 so the transition window only handles overflow/restock, not the full initial load.
- Designate one associate as "traffic controller" at the elevator bank to prevent bottlenecks and ensure bins go to the correct floor.

---

### Phase 4 — In-Venue Sales (T+0:00 to Lights Out / 19:00–~halftime)

#### 4A. Staffing Deployment — Inside Stadium

| Role | Count | Location | Responsibility |
|---|---|---|---|
| POS Cashier | 8 | 9 indoor tents (shared across clusters) | Ring sales |
| Tent Lead | 4 | 1 per tent cluster + VIP | Product knowledge, display management |
| VIP Lounge | 2 | VIP room | Dedicated to ~120 VIP guests, curated selection |
| Cart Operators | 4 | Roaming concourse | Bubble wand carts — deploy 1hr before Lights Out |
| Restockers | 2 | BOH → indoor tents | Keep tents filled from BOH reserves |
| BOH / Inventory | 4 | BOH / Basement | Counting product, packing chests for next stop, printer/POS support |
| Floater | 2 | Roaming | Break relief, volume spikes |
| **Total Inside** | **26** | | |

*Note: 4 associates released after Block Party teardown (from the 30 total), or retained as additional floaters if venue complexity warrants it.*

#### 4B. Cart Operations — Bubble Wands / Light-Up Items

| Time | Action |
|---|---|
| T+2:00 (~1hr before Lights Out) | Carts loaded and begin roaming concourse |
| T+2:30 | Increase cart density near main seating sections |
| Lights Out -10min | Final push — carts positioned at high-traffic exits from seating |
| Lights Out | Carts return to BOH, remaining inventory counted |

---

### Phase 5 — Lights Out & Post-Game (Halftime break through end)

| Step | Action | Owner |
|---|---|---|
| 1 | Indoor tents process final sales during 30-min Lights Out break | Cashiers |
| 2 | As foot traffic dies, begin consolidating tent stock → BOH | Restockers |
| 3 | POS terminals powered down, secured, returned to BOH for charging | Tech Lead |
| 4 | All remaining inventory counted and packed into chests | BOH Team |
| 5 | Chests loaded into trailers | Logistics Lead |
| 6 | Final walkthrough — nothing left behind | Ops Manager |

---

## Technical Systems: Reliability Plan

### Printer Connectivity (Addresses JAX Issues #1 and #2)

| Control | Detail |
|---|---|
| Pre-event validation | All printers powered on, calibrated, and test-printed T-24h. Ink ribbon seating verified (latch into divot — root cause of JAX Issue #1) |
| Spare hardware | Carry 1 backup printer per 4 active units. At JAX, 2 of 4 went offline — 50% failure rate is unacceptable without redundancy |
| Connectivity protocol | If a printer drops offline: (1) power cycle, (2) re-pair from Insight dashboard, (3) swap to backup if not resolved in 5 min. Do not let associates burn time troubleshooting |
| Escalation | If >1 printer fails and backup is deployed, immediately notify RIOT + Solutions Engineer. Document printer serial numbers and failure mode |

### Shopify → Insight Catalog Sync (Addresses JAX Issue #3)

| Control | Detail |
|---|---|
| T-24h sync check | Manually trigger a catalog sync and verify every SKU resolves in Insight. Screenshot confirmation |
| T-2h sync check | Re-verify sync. If any SKUs are missing, manually add them in Insight as a workaround and flag to RIOT |
| During event | Designate one BOH associate as "tech monitor" — checks sync status every 30 min and reports discrepancies immediately |
| Escalation path | RIOT contact (Jace) on speed dial. If catalog sync fails during event, fall back to manual price entry at POS as last resort — do not stop selling |

---

## RFID Gate Integration: Mixed-Environment Mitigation Plan

### The Problem

On this tour, RFID reading gates will be deployed at some merch tents but not all. This creates a hybrid environment where:

- A customer buys a tagged item at a non-gated tent (Block Party, smaller indoor tent, or roaming cart)
- That customer later walks past a gated tent carrying their purchase
- The gate reads the still-active RFID tag and could trigger a false transaction or flag

Bubble wand carts make this especially acute — carts roam the concourse with no fixed point of sale, no gate, and customers carrying purchased wands will repeatedly pass gated tent clusters throughout the event.

### Mitigation Strategy: Deactivate at Point of Sale, Not at Gate

The only reliable way to prevent double-charges in a mixed-gate environment is to kill the RFID tag at the moment of sale, regardless of whether that sale point has a gate.

#### Tier 1 — RFID Deactivation at Every POS (Preferred)

| Control | Detail |
|---|---|
| Handheld RFID deactivators at every POS | Equip every cashier station — gated tents, non-gated tents, and carts — with a handheld RFID kill device. After payment completes, cashier taps the tag to deactivate before bagging |
| Cart operators carry deactivators | Each bubble wand cart gets a handheld unit clipped to the cart. Operator deactivates the wand's tag immediately after the sale, on the spot |
| Deactivation = part of the transaction flow | Train cashiers: scan → pay → deactivate → bag. It's not an optional step. Build it into POS training during Phase 1 |
| Verification | At gated tents, the gate itself serves as a verification layer — if a deactivated item passes through and doesn't trigger, the process is working. If it does trigger, that's a training gap to address immediately |

**Why this works:** It doesn't matter whether the tent has a gate or not. Every item leaves every sale point dead. Gates become a shrink-prevention tool only, not a transaction trigger, and a purchased item can never be misread.

#### Tier 2 — Gate Configuration as Shrink-Only (If Deactivators Are Unavailable for All Points)

If handheld deactivators can't be sourced for every POS and cart in time:

| Control | Detail |
|---|---|
| Gates set to alert-only mode | RFID gates at equipped tents trigger an audible/visual alert but do NOT auto-charge or auto-flag a transaction. They function as shrink deterrents only |
| Associate posted at every gate | A dedicated associate at each gated tent visually confirms: is the person carrying a bag (already purchased) or concealing an item? The human makes the call, not the gate |
| Bag = proof of purchase | The clear plastic bags already handed out at merch tents become the visual indicator. If a customer is carrying a bagged item past a gate, the gate associate waves them through. No bag + gate alert = investigate |
| Cart-sold items get bagged too | Bubble wand cart operators must bag every sold item, even single wands. The bag is the customer's "passport" past gated tents |

**Why this works as a fallback:** It removes the double-charge risk entirely by taking gates out of the transaction chain. The tradeoff is you need an associate at each gate and you lose some automation, but you eliminate false charges.

#### Tier 3 — Hybrid (Recommended Realistic Approach for Tour Launch)

Most likely, you'll have deactivators at gated tents (they often come integrated) but not at non-gated tents and carts. So combine:

| Sale Point | Has Gate? | Has Deactivator? | Protocol |
|---|---|---|---|
| Block Party tents (outside) | No | Equip with handheld | Deactivate at POS after payment |
| Gated indoor tents | Yes | Yes (integrated) | Gate deactivates on exit after payment confirmed |
| Non-gated indoor tents | No | Equip with handheld | Deactivate at POS after payment |
| VIP Lounge | No | Equip with handheld | Deactivate at POS after payment |
| Bubble wand carts | No | Equip with handheld (clipped to cart) | Operator deactivates immediately after sale |

**Handheld deactivator count needed:** One per non-gated POS + one per cart. Based on JAX numbers: ~8 non-gated POS stations + 4 carts = 12 handheld units + 2 spares = **14 total**.

### Bubble Wand Carts — Specific Considerations

Bubble wands are the highest-risk item because:
- They're sold from a moving cart with no fixed infrastructure
- Customers carry them openly (not bagged by default) for the rest of the event
- They pass gated tents repeatedly as they move through the concourse

| Control | Detail |
|---|---|
| Pre-deactivate option | If wands are low-SKU-count (one or two variants), consider deactivating all RFID tags in BOH before loading carts. Wands leave the cart already dead. Shrink risk on carts is managed by inventory count (load count vs. cash collected) rather than RFID |
| If tags must stay live on cart | Operator deactivates with handheld after each sale. Wand goes into a branded bag. Customer has visual proof of purchase |
| Cart inventory reconciliation | At end of each cart run: remaining wands + cash/card total must reconcile to load count. This replaces RFID as the shrink control for cart-sold items |

### Training Addition (Phase 1)

Add to the existing training tracks:

| Track | Addition |
|---|---|
| Track 1 — POS Cashiers | Add 10 min: "RFID deactivation as part of transaction flow." Practice: scan → pay → deactivate → bag. Emphasize: every item, every time, no exceptions |
| Track 3 — Cart Operators | Add 10 min: "Handheld deactivator use on cart." Practice deactivating a wand, bagging it, handing it off. If pre-deactivated in BOH, train on bag-every-sale protocol instead |
| Gate Associates (new) | 15 min briefing: gate alert response protocol. Bag = purchased, no bag + alert = politely verify. Never accuse — ask "Can I help you find your receipt?" |

### Venue-to-Venue: RFID Gate Deployment Matrix

Add this to the advance site survey (Phase 0, T-48h):

| Question | Why It Matters |
|---|---|
| How many tent locations will have RFID gates? | Determines handheld deactivator count needed |
| What is the gate mode? (auto-charge vs. alert-only vs. shrink-only) | Determines whether Tier 1, 2, or 3 protocol applies |
| Are gates positioned where cart traffic will pass? | If yes, either pre-deactivate cart inventory or ensure cart operators are trained and equipped |
| Is there power at gate locations? | Gates need power — confirm during site survey, not on game day |
| What is the gate read range? | Wider range = more false reads from passersby. May need to adjust gate sensitivity or narrow the read zone with shielding |

---

## Staffing Summary (30 Associates)

| Phase | Outside | Inside | BOH | Roaming/Carts | Total |
|---|---|---|---|---|---|
| Block Party (Phase 2) | 18 | 4 (VIP setup) | 4 (staging) | 4 (training/standby) | 30 |
| Transition (Phase 3) | 12 (teardown) | 8 (receiving) | 6 (sorting) | 4 (cart prep) | 30 |
| In-Venue (Phase 4) | 0 | 18 | 6 | 6 (carts + floaters) | 30 |
| Post-Game (Phase 5) | 0 | 8 (final sales) | 16 (packout) | 6 (consolidation) | 30 |

Every associate has a defined role in every phase. No idle time.

---

## Venue-to-Venue Adaptations

Not every stop will have JAX's basement room with tables and chairs. Plan for the worst case:

| Variable | Best Case (JAX) | Worst Case | Mitigation |
|---|---|---|---|
| BOH space | Dedicated room with power | Open hallway or tent-side only | Bring folding tables, power strips, and a portable canopy for printer/POS staging |
| Freight elevator | Available (limited) | None | Pre-stage 100% of indoor tent stock before Block Party opens. Transition window handles restock only, carried by hand via stairs |
| Storage closets | 1-2 available | None | All restock pulled from trailer. Assign 1 additional restocker to compensate for longer pull distance |
| Tent count inside | 9 tents + VIP | Fewer, smaller spaces | Reduce inside cashier count proportionally. Shift headcount to cart operations for roaming sales |

---

## Quick-Reference: Tagging & Loyalty Opportunities

| Item | JAX Status | Recommendation |
|---|---|---|
| Markers ($3) | Not tagged — in POS only | Tag them. Untagged items slow down POS lookup and create shrink risk. Pre-print tags in BOH during Phase 0 |
| Clear plastic bags | Given out at tents, no branding | Opportunity: Print bags with QR code linking to loyalty signup or post-event survey. Low cost, high capture rate given avg basket of 6-8 items per family |
| Glowing wristbands | Velcro this year, switching to plastic next year | If switching to cheaper bands, reinvest margin delta into branded packaging or a "scan to register your band" digital experience |

---

## Summary

This plan converts the JAX Game 1 observations into a repeatable touring playbook. The core changes are:
1. Shift hardware and catalog validation to T-24h — stop discovering tech issues at game time
2. Restructure the Block Party layout so merch queues don't block stadium ingress
3. Right-size tent staffing (eliminate unnecessary runners) and redeploy labor to queue management and restocking
4. Pre-label all merchandise bins before the Block Party → Stadium transition to eliminate mix-up risk
5. Build redundancy into the printer fleet and establish a clear escalation path for catalog sync failures
6. Ensure every associate has a defined role in every phase — zero idle time
7. Mitigate RFID double-charge risk in mixed-gate environments by deactivating tags at point of sale — not at the gate — with specific protocols for roaming bubble wand carts

*Prepared by: Solutions Engineering*
*Based on: Cosmic JAX, FL — Game 1 Field Notes (03/19)*
