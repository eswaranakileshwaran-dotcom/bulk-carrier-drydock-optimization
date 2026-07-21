# Process Task Data — Bulk Carrier Dry Dock

> Original 5-year dry dock baseline (superseded scope, kept for reference)

## Vessel Reference
- **Type:** Panamax Bulk Carrier
- **DWT:** ~75,000 DWT
- **LOA:** ~225 m
- **Dock type:** Graving dock
- **Time unit used throughout:** Hours
- **Docking cycle:** 5-year Special Survey

## Data Sources & References

| # | Source | Used For |
|---|--------|---------|
| 1 | [IMO SOLAS Regulations — Chapter II-1](https://www.imo.org) | 5-year docking frequency requirement |
| 2 | [Teekay Corporation — Step by Step Dry Docking (2016)](https://www.teekay.com/blog/2016/04/18/step-step-glimpse-dry-docking-process/) | Hull wash, blasting, painting sequence and description |
| 3 | [Dev & Saha (2015) — Ship Repairing Time Study, 586 cargo ships](https://scispace.com/pdf/dry-docking-time-and-labour-46slnefmiw.pdf) | Task duration benchmarks, labour estimates |
| 4 | [Marine Inspection — Dry Dock Preparation Guide](https://marineinspection.app/blog/dry-dock-preparation-united-states) | Planning timelines, cost ranges |
| 5 | [Nautilus Shipping — Dry Dock Planning Guide](https://www.nautilusshipping.com/news-and-insights/dry-dock-planning-a-practical-guide-for-safer-smarter-vessel-maintenance-for-maritime-operations) | Routine vs major dock duration (10–14 days vs extended) |
| 6 | [Diesel Duck Engineering Forum](https://www.dieselduck.info/forum/viewtopic.php?t=77) | Engine overhaul timing, dock duration industry experience |
| 7 | [Marine Insight — Dry Dock Types and Requirements](https://www.marineinsight.com/guidelines/dry-dock-types-of-dry-docks-requirements-for-dry-dock/) | Dock dewatering time (8–10 hrs), block placement procedure |
| 8 | [Quora — Dry Dock Costs](https://www.quora.com/How-much-does-dry-docking-a-ship-for-repairs-cost-What-are-the-costs-involved) | Cost ranges by vessel type and scope |

## Duration Notation
All durations written as TRIA(min, mode, max) in hours.
This is the triangular distribution used in Arena DES —
min = best case, mode = most likely, max = worst case.

---

## Phase 1 — Vessel Arrival & Docking
**Type:** Sequential (each task must finish before next starts)
**Critical path:** Yes — no parallel work until ship is secured on blocks

| # | Task | Duration TRIA (hrs) | Workers | Resource | Predecessor |
|---|------|-------------------|---------|----------|-------------|
| 1.1 | Port formalities & pilot boarding | TRIA(3, 4, 5) | 2 | Harbor pilot | — |
| 1.2 | Tug assist & vessel maneuvering | TRIA(2, 3, 4) | 6 | Tug crew + dockmaster | 1.1 |
| 1.3 | Block alignment & dive team check | TRIA(1.5, 2, 3) | 4 | Dive team | 1.2 |
| 1.4 | Dock gate closure | TRIA(0.5, 1, 1.5) | 2 | Dock operator | 1.3 |
| 1.5 | Dock dewatering (pump out) | TRIA(8, 10, 12) | 2 | Pump operator | 1.4 |
| 1.6 | Stability confirmation on blocks | TRIA(0.5, 1, 1.5) | 3 | Dockmaster + surveyor | 1.5 |
| 1.7 | Shore power connection | TRIA(1.5, 2, 3) | 2 | Electrician | 1.6 |
| 1.8 | Scaffolding erection | TRIA(6, 8, 10) | 10 | Scaffold crew | 1.6 |

**Phase 1 critical path total:** ~31 hours

---

## Phase 2 — Hull Work
**Type:** Partially parallel (blasting zones run simultaneously, painting waits for blasting)
**Note:** This is the primary bottleneck phase — largest surface area, most equipment-constrained

| # | Task | Duration TRIA (hrs) | Workers | Equipment | Priority | Predecessor |
|---|------|-------------------|---------|-----------|----------|-------------|
| 2.1 | HP freshwater wash | TRIA(12, 16, 20) | 6 | 3× HP wash units | Critical | 1.8 |
| 2.2 | Hull visual inspection + UT scan | TRIA(20, 24, 32) | 4 | UT gauges | Critical | 2.1 |
| 2.3 | Grit blasting — topsides (40% area) | TRIA(40, 48, 60) | 8 | 4× blast machines | Critical | 2.1 |
| 2.4 | Grit blasting — boot top (60% area) | TRIA(30, 36, 48) | 6 | 3× blast machines | Critical | 2.1 |
| 2.5 | Grit blasting — bottom (5% area) | TRIA(10, 12, 16) | 4 | 2× blast machines | High | 2.1 |
| 2.6 | Steel thickness reporting | TRIA(12, 16, 20) | 2 | UT equipment | High | 2.2 |
| 2.7 | Steel renewal (contingency) | TRIA(48, 72, 120) | 8 | Welding machines + crane | Critical | 2.6 |
| 2.8 | Primer coat application | TRIA(20, 24, 30) | 6 | Airless spray units | Critical | 2.3, 2.4, 2.5 |
| 2.9 | Anti-corrosion paint — hull sides | TRIA(20, 24, 30) | 6 | Airless spray units | Critical | 2.8 |
| 2.10 | Anti-fouling paint — bottom | TRIA(20, 24, 30) | 6 | Airless spray units | Critical | 2.9 |
| 2.11 | Zinc anode replacement | TRIA(6, 8, 10) | 4 | Drill + bolts | High | 2.5 |
| 2.12 | ICCP system inspection | TRIA(3, 4, 5) | 2 | ICCP test equipment | Medium | 2.11 |

**Phase 2 critical path (sequential):** ~192 hours
**With parallel blasting zones:** ~144 hours
**Bottleneck resource:** Blast machines (4 units shared across 3 zones)

---

## Phase 3 — Underwater Appendages
**Type:** Parallel with Phase 2
**Note:** Shares the crane with Phase 2 steel renewal — creates queuing conflict

| # | Task | Duration TRIA (hrs) | Workers | Equipment | Priority | Predecessor |
|---|------|-------------------|---------|-----------|----------|-------------|
| 3.1 | Propeller removal & inspection | TRIA(6, 8, 10) | 4 | Crane + hydraulic jack | Critical | 1.6 |
| 3.2 | Propeller blade repair & polish | TRIA(20, 24, 30) | 3 | Grinder + polish tools | High | 3.1 |
| 3.3 | Propeller reinstallation & torque | TRIA(6, 8, 10) | 4 | Crane + hydraulic jack | Critical | 3.2 |
| 3.4 | Propeller shaft withdrawal | TRIA(12, 16, 20) | 4 | Hydraulic press + crane | High | 3.1 |
| 3.5 | Shaft bearing inspection & renewal | TRIA(10, 12, 16) | 3 | Bearing puller + gauges | High | 3.4 |
| 3.6 | Shaft reinstallation & alignment | TRIA(10, 12, 16) | 4 | Laser alignment tool | Critical | 3.5 |
| 3.7 | Stern tube seal renewal | TRIA(12, 16, 20) | 4 | Seal press tools | Critical | 3.4 |
| 3.8 | Rudder inspection | TRIA(6, 8, 10) | 3 | Feeler gauges + calipers | High | 1.6 |
| 3.9 | Rudder bearing renewal | TRIA(20, 24, 30) | 4 | Hydraulic tools + crane | High | 3.8 |
| 3.10 | Rudder reinstallation & test | TRIA(6, 8, 10) | 3 | Crane | Critical | 3.9 |
| 3.11 | Sea chest cleaning & painting | TRIA(10, 12, 16) | 4 | HP washer + spray unit | High | 1.6 |
| 3.12 | Sea valve inspection & overhaul | TRIA(12, 16, 20) | 4 | Valve tools + gaskets | Critical | 3.11 |
| 3.13 | Anchor chain ranging & measurement | TRIA(6, 8, 10) | 4 | Measuring tape | Medium | 1.6 |
| 3.14 | Bottom plug inspection & refit | TRIA(3, 4, 5) | 2 | Plug tools | Low | 1.6 |
| 3.15 | Bilge keel inspection & repair | TRIA(6, 8, 10) | 3 | Welding machine | Medium | 2.5 |

**Phase 3 critical path:** ~120 hours
**Bottleneck resource:** Crane (1 unit — shared with Phase 2 steel renewal)

---

## Phase 4 — Engine Room & Machinery
**Type:** Parallel with Phases 2, 3, 5
**Note:** Many tasks run simultaneously — bottleneck is certified engine technicians (5 available)

| # | Task | Duration TRIA (hrs) | Workers | Equipment | Priority | Predecessor |
|---|------|-------------------|---------|-----------|----------|-------------|
| 4.1 | Main engine top overhaul | TRIA(60, 72, 96) | 5 | Engine lifting beam | Critical | 1.7 |
| 4.2 | Piston & liner inspection | TRIA(40, 48, 64) | 4 | Hydraulic press | High | 4.1 |
| 4.3 | Turbocharger overhaul | TRIA(20, 24, 32) | 3 | Turbo tools | High | 4.1 |
| 4.4 | Fuel injection pump overhaul | TRIA(12, 16, 20) | 2 | Pump bench | High | 1.7 |
| 4.5 | Auxiliary engine overhaul (×2) | TRIA(40, 48, 64) | 4 | Engine tools | High | 1.7 |
| 4.6 | Main seawater pump overhaul | TRIA(10, 12, 16) | 2 | Pump tools | Medium | 3.12 |
| 4.7 | Fresh water generator service | TRIA(6, 8, 10) | 2 | Basic tools | Low | 1.7 |
| 4.8 | Boiler inspection & cleaning | TRIA(12, 16, 20) | 3 | Boiler tools | High | 1.7 |
| 4.9 | Oily water separator service | TRIA(6, 8, 10) | 2 | OWS tools | Medium | 1.7 |
| 4.10 | Ballast pump overhaul | TRIA(10, 12, 16) | 2 | Pump tools | High | 1.7 |
| 4.11 | Air compressor overhaul | TRIA(6, 8, 10) | 2 | Compressor tools | Medium | 1.7 |
| 4.12 | Heat exchanger cleaning | TRIA(12, 16, 20) | 3 | Tube cleaning equipment | High | 1.7 |
| 4.13 | Steering gear inspection | TRIA(6, 8, 10) | 2 | Hydraulic tools | Critical | 3.10 |
| 4.14 | Electrical switchboard inspection | TRIA(6, 8, 10) | 2 | Electrical test kit | High | 1.7 |
| 4.15 | Navigation equipment service | TRIA(6, 8, 10) | 2 | Calibration tools | Medium | 1.7 |

**Phase 4 if fully sequential:** ~312 hours
**Phase 4 with parallel tasks (realistic):** ~120 hours
**Bottleneck resource:** Engine technicians — only 5 certified, 1-shift operation

---

## Phase 5 — Tank & Structural Inspections
**Type:** Parallel with Phases 2, 3, 4
**Note:** Confined space entry rules require minimum 3 workers per space (2 inside + 1 standby)

| # | Task | Duration TRIA (hrs) | Workers | Equipment | Priority |
|---|------|-------------------|---------|-----------|----------|
| 5.1 | Ballast tank entry, clean & inspect | TRIA(40, 48, 64) | 6 | Blowers + lighting + UT | Critical |
| 5.2 | UT thickness survey — tank plating | TRIA(20, 24, 32) | 2 | UT equipment | High |
| 5.3 | Tank coating — epoxy (if required) | TRIA(40, 48, 64) | 6 | Spray + forced ventilation | High |
| 5.4 | Cargo hold cleaning & inspection | TRIA(20, 24, 32) | 8 | Industrial vacuum | High |
| 5.5 | Hold coating (if required) | TRIA(40, 48, 64) | 6 | Spray equipment | Medium |
| 5.6 | Void space inspection | TRIA(12, 16, 20) | 2 | Confined space entry kit | High |
| 5.7 | Fuel oil tank inspection | TRIA(10, 12, 16) | 3 | Confined space kit | Medium |

**Phase 5 critical path:** ~96 hours
**Constraint:** Confined space entry — 3 workers minimum per space, cannot parallelize beyond available teams

---

## Phase 6 — Class Society Surveys
**Type:** Interspersed — triggered when prerequisite work is complete
**Note:** Single surveyor is a hard constraint — creates approval gate delays of 8–16 hrs on average

| # | Survey | Duration TRIA (hrs) | Ship Staff | Inspector | Triggered After |
|---|--------|-------------------|-----------|-----------|----------------|
| 6.1 | Hull structure survey | TRIA(6, 8, 12) | 2 | Class surveyor | Phase 2 blasting |
| 6.2 | Propeller & shaft survey | TRIA(3, 4, 6) | 2 | Class surveyor | Task 3.4 |
| 6.3 | Main engine survey (CMS) | TRIA(6, 8, 12) | 2 | Class surveyor | Task 4.1 |
| 6.4 | Boiler survey | TRIA(3, 4, 6) | 1 | Class surveyor | Task 4.8 |
| 6.5 | Load line survey | TRIA(3, 4, 6) | 2 | Class + flag surveyor | Near completion |
| 6.6 | Safety equipment survey | TRIA(3, 4, 6) | 2 | Class surveyor | Near completion |
| 6.7 | MARPOL compliance check | TRIA(3, 4, 6) | 1 | Port state surveyor | Mid-docking |

**Total survey hours (active):** ~36 hours
**Surveyor wait/delay distribution:** TRIA(0, 4, 24) hours per survey gate

---

## Phase 7 — Undocking & Sea Trials
**Type:** Sequential — cannot begin until all surveys cleared
**Critical path:** Yes

| # | Task | Duration TRIA (hrs) | Workers | Equipment | Priority |
|---|------|-------------------|---------|-----------|----------|
| 7.1 | Scaffolding removal | TRIA(6, 8, 10) | 10 | — | High |
| 7.2 | Dock flooding (refloating) | TRIA(8, 10, 12) | 2 | Dock pumps | Critical |
| 7.3 | Final stability check | TRIA(1.5, 2, 3) | 3 | — | Critical |
| 7.4 | Tug assist out of dock | TRIA(2, 3, 4) | 6 | Tugs | Critical |
| 7.5 | Sea trials — propulsion & steering | TRIA(10, 12, 16) | 8 | Ship crew + inspector | Critical |
| 7.6 | Anchor & chain test | TRIA(1.5, 2, 3) | 4 | — | High |
| 7.7 | Class certification sign-off | TRIA(3, 4, 6) | 2 | Class surveyor | Critical |
| 7.8 | Vessel return to service | 1 | — | — | — |

**Phase 7 total:** ~27 hours

---

## Current State Summary

| Metric | Value |
|--------|-------|
| Total dock duration (current) | ~720 hours (30 days) |
| Target dock duration | 432–528 hours (18–22 days) |
| Improvement target | 30–40% reduction |
| Off-hire cost rate | $15,000–$25,000 per day |
| Potential savings per docking | $120,000–$300,000 |
