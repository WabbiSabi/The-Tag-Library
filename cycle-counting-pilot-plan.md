# RFID Cycle Counting — Pilot Rollout Plan

## Overview

This plan defines the phased rollout of RFID-based cycle counting operations, progressing from foundational tagging and induction through inventory movement, state management, and EPC lifecycle hygiene.

---

## Phase R0 — Foundation (Ready)

Establishes the baseline: every item is tagged, inducted into a location, and verifiable via inventory check.

### ① On Product — "Item Properly Tagged"

| Attribute       | Detail                                      |
|-----------------|----------------------------------------------|
| Description     | Each item has a valid RFID tag applied        |
| Scope           | Warehouse                                     |
| Milestone       | 100% of SKUs in pilot scope are tagged        |
| Dependencies    | Tag procurement, encoding standards (UPC, TID → EPC mapping) |
| Acceptance      | Every item in scope has a scannable, encoded EPC tied to its UPC |

### ② Induct — "Assigned to Store / WH / WIP"

| Attribute       | Detail                                      |
|-----------------|----------------------------------------------|
| Description     | Tagged item is assigned to a specific site and marked "Ready" |
| Scope           | Site (Store, Warehouse, or WIP location)      |
| Milestone       | All tagged items in pilot locations are inducted |
| Dependencies    | Phase R0 ① (On Product) complete              |
| Acceptance      | Each EPC is associated with exactly one site in the system of record |

### ③ Inventory Check — "Still in Store / WH / WIP"

| Attribute       | Detail                                      |
|-----------------|----------------------------------------------|
| Description     | Confirms an inducted item is still physically present at its assigned site |
| Scope           | Site                                          |
| Milestone       | Cycle count read rates meet accuracy threshold (target: ≥ 95%) |
| Dependencies    | Phase R0 ② (Induct) complete                  |
| Acceptance      | System can reconcile expected vs. read EPCs per site and surface discrepancies |

### R0 Exit Criteria

- All pilot items tagged and encoded
- Induction records exist for every EPC at every pilot site
- Inventory check process runs end-to-end with discrepancy reporting

---

## Phase P1 — Movement & State Management

Introduces the ability to track item state changes and physical transfers between sites.

### ④ State Change — "Not Ready / Problem Solve"

| Attribute       | Detail                                      |
|-----------------|----------------------------------------------|
| Description     | Flag an item as unavailable or requiring investigation |
| Scope           | Site                                          |
| States          | `not ready`, `problem solve`                  |
| Milestone       | State change events are captured and visible in reporting |
| Dependencies    | Phase R0 complete                             |
| Acceptance      | An item's state can be updated at the site level; state history is auditable |

### ⑤ Move / Transfer — "Tagged Product Moving Elsewhere"

| Attribute       | Detail                                      |
|-----------------|----------------------------------------------|
| Description     | Record the departure of an item from one site and its arrival at another |
| Scope           | Site (From / Both / Hold) or Site #2          |
| Direction       | Departure → Arrival                          |
| Milestone       | Inter-site transfers reflected in total count records at both origin and destination |
| Dependencies    | Phase R0 complete; receiving site must also be onboarded |
| Acceptance      | Transfer event decrements origin count and increments destination count; total count record is maintained |

### △ Bridge Sold — Tag Decommission

| Attribute       | Detail                                      |
|-----------------|----------------------------------------------|
| Description     | When an item is sold, bridge the sale event to tag decommissioning |
| Scope           | Site (POS integration)                        |
| Milestone       | Sold items are automatically flagged for tag decommission |
| Dependencies    | POS / sale event feed available                |
| Acceptance      | Sold EPCs no longer appear in active inventory counts |

### P1 Exit Criteria

- State changes are tracked and reportable per site
- Transfers between pilot sites update counts on both ends
- Sold items trigger tag decommission flow

---

## Phase P1.5 — EPC Hygiene

Focuses on cleaning up the EPC population to maintain data integrity over time.

### ⑥ Retire / Delete EPC — "EPC Hygiene / Scrub"

| Attribute       | Detail                                      |
|-----------------|----------------------------------------------|
| Description     | Remove stale, orphaned, or decommissioned EPCs from the active dataset |
| Scope           | System-wide                                   |
| Milestone       | Automated scrub process runs on a defined cadence |
| Dependencies    | Phase P1 complete (state changes and transfers feeding retirement signals) |
| Acceptance      | Retired EPCs are archived, not deleted; active EPC pool reflects only live inventory |

### P1.5 Exit Criteria

- EPC scrub job runs without manual intervention
- No retired/sold EPCs appear in active cycle counts
- Audit trail preserved for all retired EPCs

---

## Encoding Reference

| Identifier | Role                                |
|------------|--------------------------------------|
| UPC        | Product-level identifier             |
| TID        | Tag-level hardware identifier        |
| EPC        | Unique item-level identifier (encoded from TID, mapped to UPC) |

---

## Site Requirements

| Requirement                  | R0 | P1 | P1.5 |
|------------------------------|----|----|------|
| RFID readers / handhelds     | ✅ | ✅ | —    |
| Tag encoding station         | ✅ | —  | —    |
| Network connectivity at site | ✅ | ✅ | ✅   |
| POS integration              | —  | ✅ | —    |
| EPC management system        | ✅ | ✅ | ✅   |
| Reporting / dashboard        | ✅ | ✅ | ✅   |

---

## Dependency Graph

```
① On Product
   └──▶ ② Induct
         └──▶ ③ Inventory Check
               ├──▶ ④ State Change
               ├──▶ ⑤ Move / Transfer
               ├──▶ △ Bridge Sold
               └──────────────▶ ⑥ Retire / Delete EPC
```

---

## Open Questions

- [ ] What accuracy threshold is acceptable for Phase R0 inventory checks?
- [ ] Which pilot sites are in scope for Phase P1 transfers?
- [ ] What cadence for the EPC hygiene scrub (daily, weekly)?
- [ ] How does "problem solve" state integrate with existing exception workflows?
- [ ] Is "Bridge Sold" a hard dependency for P1 or can it run in parallel with P1.5?
