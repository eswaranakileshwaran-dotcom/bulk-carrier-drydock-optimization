# Arena Simulation & Scenario Testing Design
This is the build spec for the Arena model. It reads durations from
`07_process_task_data.md`, resources from `08_resource_data.md`
(including the banking berth rules), and applies the cost formula from
`09_cost_data.md` to every run's output. The baseline this model
replicates is the Current State VSM in `10_vsm_data.md`.

## Model entities

**Entity:** Vessel, arriving for 20-year Special Survey dry docking.

Each vessel entity carries attributes:
- Steel tonnage (sampled 600–800 t per arrival, not fixed)
- Arrival timestamp
- Berthing state while waiting: none / double-banked / triple-banked
  (assigned by the banking rule below, not chosen by the entity)

## Baseline (as replicated from the VSM)

- 1 vessel in the system at a time
- No queue, no banking
- Repair berth used for T11/T12 as standard practice (not a scenario —
  this is fixed in both the VSM and here)
- All durations per `07_process_task_data.md`, steel renewal split
  sequential across T05a→T05b→T05c (single steel crew)
- Resources per `08_resource_data.md`: 1 dry dock, 2 repair berths, 1
  banking berth (unused in baseline), 2 cranes

Run this first, alone, to confirm the model reproduces the VSM's
24–53 day lead-time range before any scenario is layered on. If it
doesn't match, fix the model before trusting any scenario output.

## Scenario 1 — Yard Congestion (ship count)

**Parameter varied:** number of vessels concurrently in the system.
**Levels:** 1, 2, 3, 4 ships.
**Held fixed:** arrival rate (moderate, not stressed), no banking.
**Logic:** vessels arrive per a fixed inter-arrival distribution; only
one can occupy the dry dock at a time; additional vessels wait at
anchorage (unbanked) until the dock is free.
**Outputs to record per ship-count level:**
- Dock utilization %
- Anchorage queue wait time (mean, max)
- Total vessel time-in-system
**What "best" means here:** the ship count where dock utilization is
high but queue wait hasn't started climbing steeply — not the highest
ship count tested.

## Scenario 2 — Excess Arrivals vs. Capacity

**Parameter varied:** inter-arrival time (arrival rate), at the ship
count identified as the sweet spot in Scenario 1.
**Levels:** step the mean inter-arrival time down progressively (e.g.
20%, 10%, 5% shorter each run) from a comfortable baseline toward the
yard's theoretical throughput limit.
**Held fixed:** ship-count logic from Scenario 1, no banking.
**Outputs to record per arrival-rate level:**
- Queue length over time (does it stabilize or keep climbing?)
- Point at which queue stops converging to a steady wait
**What "best" means here:** not a best case — this scenario's output is
a **breaking point** (the arrival rate the yard can't absorb), used as
a ceiling to test the realistic arrival rate against, not a value to
optimize.

## Scenario 3 — Banking (double/triple)

**Parameter varied:** berthing state assigned to a vessel while it
queues for the dock.
**Levels:** none (anchored) / double-banked / triple-banked.
**Held fixed:** run conditional on Scenario 1's identified sweet-spot
ship count and Scenario 2's realistic arrival rate — not in isolation
at 1 ship, since banking is a response to congestion, not a
free-standing choice (per the earlier discussion).
**Logic:**
- A queuing vessel is assigned to the banking berth once it's occupied
  by 1 (double) or 2 (triple) other vessels
- Crane-dependent tasks (T05a–c, T07) get the multiplier from
  `08_resource_data.md`'s banking berth rules table: none / +15–25% /
  +30–50%
- Triple-banked, crane-unreachable tasks are **blocked** (precedence
  constraint) until the vessel re-berths inboard or a mobile crane is
  modeled as available — confirm this assumption with the yard before
  running
**Outputs to record per banking level:**
- Total vessel time-in-system (does starting early under a banking
  penalty beat waiting clean at anchor?)
- Crane utilization and contention between banked vessels
**What "best" means here:** the banking level (if any) where earlier
start time outweighs the crane-task slowdown, net of any blocked-task
delay from the reach limit.

## Combined run

Since banking is conditional on congestion, the combined test is a
2-factor grid rather than a 3-factor one (offload is out — it's fixed
in the baseline):

| Ship count (Scenario 1) | Banking state (Scenario 3) |
|---|---|
| Sweet-spot count from Scenario 1 | None |
| Sweet-spot count from Scenario 1 | Double |
| Sweet-spot count from Scenario 1 | Triple |
| One level above sweet-spot | None |
| One level above sweet-spot | Double |
| One level above sweet-spot | Triple |

Run all six; this shows whether banking meaningfully rescues a
congestion level that would otherwise be over the sweet spot, or
whether the crane penalty (and any blocked tasks) cancels the benefit.

## Output table (fill in after each run)

| Scenario / combination | Dock utilization % | Mean total time-in-system | Total cost (via `09_cost_data.md` formula) |
|---|---|---|---|
| Baseline | | | |
| Scenario 1 — 1/2/3/4 ships | | | |
| Scenario 2 — arrival rate steps | | | |
| Scenario 3 — none/double/triple | | | |
| Combined grid (6 rows) | | | |

Compare every row back to the analytical (hand-calculated) VSM scenario
tables in `10_vsm_data.md` — the gap between the two is exactly the
value Arena adds: queueing and resource-contention effects a static
table can't capture.
