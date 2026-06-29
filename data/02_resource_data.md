# Resource Data — Bulk Carrier Dry Dock

## Purpose
This file defines every resource used in the dry dock process.
Resources are referenced directly in the Arena DES model.
All costs in USD. Time unit = hours.

## Resource Definitions

### Human Resources (Crews)

| Resource Name | Quantity | Busy Cost ($/hr) | Idle Cost ($/hr) | Phase Used |
|---------------|----------|-----------------|-----------------|------------|
| Harbor pilot | 1 | 200 | 0 | Phase 1 |
| Dockmaster | 1 | 150 | 50 | Phase 1, 7 |
| Tug crew | 6 | 60 each | 0 | Phase 1, 7 |
| Dive team | 4 | 80 each | 0 | Phase 1 |
| Dock pump operator | 2 | 50 each | 30 each | Phase 1, 7 |
| Scaffold crew | 10 | 35 each | 0 | Phase 1, 7 |
| Shipyard electrician | 2 | 60 each | 30 each | Phase 1 |
| Blast crew | 8 | 40 each | 0 | Phase 2 |
| Painting crew | 6 | 40 each | 0 | Phase 2 |
| UT thickness surveyor | 2 | 70 each | 0 | Phase 2, 5 |
| Welding crew | 4 | 55 each | 0 | Phase 2, 3 |
| Engine technician | 5 | 75 each | 30 each | Phase 4 |
| Confined space team | 3 | 70 each | 0 | Phase 5 |
| Class surveyor | 1 | 250 | 0 | Phase 6 |
| Ship crew (sea trials) | 8 | 45 each | 45 each | Phase 7 |

### Equipment Resources

| Resource Name | Quantity | Cost ($/hr) | Shared Between | Bottleneck? |
|---------------|----------|-------------|---------------|-------------|
| Blast machine | 4 | 200 each | Phase 2 zones 2.3, 2.4, 2.5 | YES |
| Crane | 1 | 300 | Phase 2 (steel renewal) + Phase 3 (lifting) | YES |
| Airless spray unit | 4 | 100 each | Phase 2 painting tasks | No |
| HP wash unit | 3 | 80 each | Phase 2 wash | No |
| Hydraulic press | 1 | 150 | Phase 3 shaft work | No |
| Laser alignment tool | 1 | 100 | Phase 3 task 3.6 | No |
| UT gauge | 2 | 50 each | Phase 2, 5 | No |
| Welding machine | 3 | 80 each | Phase 2, 3 | No |
| Dock pumps | 2 | 120 each | Phase 1 dewater, Phase 7 flood | No |

---

## Arena Resource Setup Instructions

When setting up resources in Arena, use these exact names
(Arena is case-sensitive and spaces matter):

| Arena Resource Name | Capacity | Cost per hour (busy) |
|--------------------|----------|---------------------|
| Blast_Machine | 4 | 200 |
| Crane | 1 | 300 |
| Class_Surveyor | 1 | 250 |
| Engine_Tech | 5 | 75 |
| Scaffold_Crew | 10 | 35 |
| Blast_Crew | 8 | 40 |
| Painting_Crew | 6 | 40 |
| Dock_Pump_Op | 2 | 50 |
| Hydraulic_Press | 1 | 150 |
| Laser_Align_Tool | 1 | 100 |

> Note: In Arena, go to Basic Process panel → Resources.
> Set capacity = quantity above. Set cost under Resource Cost tab.
> Bottleneck resources (Blast_Machine, Crane, Class_Surveyor)
> are the primary targets for scenario improvement.

---

## Bottleneck Resource Summary

| Resource | Utilization (estimated) | Why it bottlenecks |
|----------|------------------------|-------------------|
| Crane (1 unit) | ~90% | Shared between Phase 2 steel renewal and Phase 3 propeller/shaft lifting — both need it simultaneously |
| Blast machines (4 units) | ~90% |

## Data Sources & References

| # | Source | Used For |
|---|--------|---------|
| 1 | [Quora — Dry Dock Costs Breakdown](https://www.quora.com/How-much-does-dry-docking-a-ship-for-repairs-cost-What-are-the-costs-involved) | Equipment and labor cost ranges |
| 2 | [Marine Inspection — Dry Dock Preparation (US)](https://marineinspection.app/blog/dry-dock-preparation-united-states) | Delay costs ($35,000–$75,000/day for emergency parts), planning timelines |
| 3 | [Dev & Saha (2015, 2016) — Dry Docking Time and Labour](https://scispace.com/pdf/dry-docking-time-and-labour-46slnefmiw.pdf) | Labour man-days benchmark for bulk carriers |
| 4 | [Teekay Corporation — Dry Docking Process](https://www.teekay.com/blog/2016/04/18/step-step-glimpse-dry-docking-process/) | Crew roles and equipment used per phase |
| 5 | [OSHA — Shipbuilding and Ship Repair: Dry Docking](https://www.osha.gov/ship-building-repair/dry-docking) | Dockmaster role, dive team requirements, safety crew standards |

> Note: Specific hourly labor rates are indicative estimates based on
> South/East Asian shipyard benchmarks. Actual rates vary significantly
> by yard location — see 03_cost_data.md for shipyard location comparison.
