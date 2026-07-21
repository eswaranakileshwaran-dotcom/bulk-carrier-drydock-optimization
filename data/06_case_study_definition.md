# Case Study Definition — 20-Year Special Survey Dry Dock

Add as `data/01_case_study_definition.md`. This replaces/supersedes any
earlier "case study scope" file that assumed the general 5-year cycle.

## Vessel
Panamax bulk carrier, ~76,000–82,000 DWT, undergoing statutory 20-year
Class renewal (Special Survey) — the survey milestone that requires the
most extensive steel and equipment work in the vessel's life.

## Work packages in scope

| # | Package | Detail | Why it's on the critical path or not |
|---|---|---|---|
| 1 | Steel renewal | 600–800 tons, in way of tank top plating, bulkheads, double bottom tanks | **Critical path** — bound by yard capacity of 15–25 t/day |
| 2 | Main engine overhaul | Full overhaul per maker's 20-year/running-hours schedule | Parallel track — runs alongside steel work, different crew |
| 3 | Auxiliary engine overhaul | All gensets, full overhaul | Parallel track |
| 4 | Auxiliary equipment overhaul | Pumps, purifiers, compressors, steering gear, windlass/mooring winches | Parallel track, can start at anchorage before docking |
| 5 | Safety & fire-fighting equipment — 20-year compliance | Lifeboats/liferafts, davits, fire pumps, hydrants, fixed fire-fighting systems — renewal/recertification | **Does not need the dry dock** — candidate to shift to repair berth work (see Arena scenario 4) |
| 6 | Hull coating | 5-year recoat cycle (underwater hull + boot top) — shorter cycle than the 20-year steel/survey interval, so this is a recoat, not a first coat | Depends on steel renewal finishing in each block before blasting/painting that block |

## Duration driver

Steel renewal is the package that sets the floor on how long the vessel
occupies the dry dock:

```
600 tons ÷ 25 t/day  = 24 days (best case, full yard capacity)
800 tons ÷ 15 t/day  = 53 days (worst case, capacity-constrained)
```

Use this 24–53 day range as the input distribution for the steel-renewal
activity in both the Gantt chart and the Arena model — not a single fixed
number. Everything else (engine overhaul, aux equipment, safety
equipment) should be checked against this range: any package that
finishes inside it is "free" (non-critical); anything that risks running
longer than the low end of the range becomes a candidate for
parallelization or moving off the dock.

## What changed from the old (5-year) scope

- Old scope: general recurring 5-year hull dry dock, steel renewal as one
  line item among many, VSM built around Panamax fleet-wide averages.
- New scope: one specific 20-year renewal case, steel tonnage and yard
  capacity given as hard numbers, and hull coating explicitly separated
  out as a shorter (5-year) cycle nested inside the 20-year event rather
  than assumed to happen at the same frequency as steel renewal.
