# Cost Data — 20-Year Special Survey (Revised Scope)
Purpose: applies cost rates to the tasks in `07_process_task_data.md`
and the resources in `08_resource_data.md`, so the Arena model can report
cost alongside time. Rates below are **indexed (base 100 = dry dock
day-rate), not real supplier quotes** — swap in your own numbers privately
if you have commercially-sensitive figures, but keep the published repo
on indexed/rounded values as agreed earlier.

## Day-rate resources

| Resource | Indexed rate (per day) | Applies to |
|---|---|---|
| Dry dock occupancy | 100 (baseline) | T03–T08, T13–T14 |
| Repair berth occupancy | 40 | T11, T12 (when routed off the dock) |
| Vessel off-hire / demurrage | 130 | Every day from T03 to T14, regardless of location — this is the owner's opportunity cost, separate from the yard's dock/berth rate |

## Per-unit / lump-sum items

| Item | Indexed cost | Basis |
|---|---|---|
| Steel renewal | 12 per ton | Applied to 600–800 t total (tank top + bulkhead + DB tanks combined) |
| Main engine overhaul | 900 lump sum | T09 |
| Auxiliary engine overhaul | 500 lump sum | T10 |
| Auxiliary equipment overhaul | 400 lump sum | T11 |
| Safety/fire-fighting equipment renewal | 350 lump sum | T12 |
| Hull blast + 5-yr recoat | 600 lump sum | T07–T08 |
| Class survey fees | 150 lump sum | T06, T13 |
| Contingency | 10% of subtotal | Applied at the end |

## How to combine these into a total

```
Total cost = (dry dock day-rate × dry-dock-occupancy days)
           + (repair berth day-rate × repair-berth days, if used)
           + (off-hire day-rate × total days vessel-in-yard)
           + steel renewal (rate × actual tons, 600–800 t)
           + lump-sum items (engine, aux equipment, safety, coating, survey)
           + 10% contingency on the above subtotal
```

This is the formula each Arena scenario run should apply to its output
duration, so the four scenarios in the Arena file can be compared on
**both** total time and total cost — not time alone. The repair-berth
offload scenario (Arena Scenario 4) is expected to look better on this
formula specifically because it trades a large avoided cost (dry dock
day-rate) for a smaller added one (repair berth day-rate), even when
total vessel-in-yard time doesn't change much.

## What to keep private vs. public

- Public repo: indexed rates as above, the combination formula, and the
  relative ranking of scenarios.
- Keep private (not committed): the actual $/day and $/ton figures from
  your real yard quotes, if those were given to you commercially — those
  belong in a local, un-tracked file (e.g. `data/09_cost_data_actuals.xlsx`
  added to `.gitignore`) that you use to convert the indexed numbers to
  real dollars for your own reporting.
