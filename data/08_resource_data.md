# Resource Data — 20-Year Special Survey (Revised Scope)

File: `data/08_resource_data.md`

Purpose: defines the resources that `07_process_task_data.md` tasks
consume. This is the direct input to the Arena model's resource blocks
(dock, repair berth, crane, crews) and to the utilization KPIs in the
Arena scenario design file (to be numbered once we get to that step —
it'll come after `09_cost_data.md` and `10_vsm_data.md`).

## Fixed yard resources

| Resource | Quantity | Notes |
|---|---|---|
| Dry dock | 1 | The scarce resource — every scenario in the Arena file is ultimately about protecting this resource's occupancy |
| Repair berth | 2 | Used for afloat work that doesn't need the dock (T11, T12) — this is standard yard practice in the baseline, not a scenario |
| Banking berth (quay position) | 1 position, max 3 vessels rafted (1 inboard + double + triple) | Distinct from the 2 repair berths above — this is the specific quay position vessels wait at when banked while queuing for the dry dock |
| Heavy crane | 2 | Shared across docked and banked vessels — this is what gets the double/triple-banking time penalty in Arena |
| Anchorage swinging room | Assume uncongested unless testing Arena Scenario 1/2 | Queue point before a dock/berth or banking position is free |

## Banking berth rules (for Scenario 3)

| Position | Crane reach | Effect on crane-dependent tasks (T05a–c, T07) |
|---|---|---|
| Inboard (against the quay) | Full reach | No penalty — treated as if berthed normally |
| Double-banked (1 vessel out) | Full reach, longer swing | +15–25% service-time multiplier |
| Triple-banked (2 vessels out) | **Reach-limited** — heavy-lift crane tasks (steel plate handling, blast equipment) may not reach the outermost vessel at all | +30–50% multiplier for tasks the crane *can* reach; tasks it can't reach are **blocked**, not delayed — they wait until the vessel is re-berthed inboard or a mobile/floating crane is brought in (model this as a precedence constraint, not a duration multiplier) |

Confirm with your yard whether a floating/mobile crane is available as a
fallback for the triple-banked reach gap — if not, Arena should treat
"triple-banked + needs heavy crane" as a hard block on those specific
tasks rather than a slowdown.

## Crew resources

| Crew | Size | Shift pattern | Applies to task(s) | Capacity/rate |
|---|---|---|---|---|
| Planning | 3 | 1×8hr | T01, T02 | — |
| Dock crew | 12–16 | 1×12hr | T03, T04, T14 | — |
| Steel crew | 1 gang (specify headcount from your yard) | 2×12hr | T05a–T05c | **15–25 tons/day** (binding constraint) |
| Class surveyor | 1 (pre-bookable) | Ad hoc, scheduled | T06, T13 | — |
| Blast/coat crew | 8–10 | 2×12hr | T07, T08 | — |
| ME team | 5–6 | 1×8hr | T09 | — |
| AE team | 4 | 1×8hr | T10 | — |
| Aux equipment team | 4–5 | 1×8hr | T11 | — |
| Safety equipment team (often sub-contracted, OEM-certified) | 2–3 | 1×8hr | T12 | — |

## Resource notes for the Arena model

- **Steel crew capacity is the one number everything else is scaled
  against.** If you later split the steel crew into two gangs to
  parallelize T05a–T05c, halve the per-task duration but keep total
  tons/day capacity the same in aggregate — don't double the yard's
  throughput without justification.
- **Crane** is the resource that carries the double/triple-banking
  penalty (Arena Scenario 3): when a vessel is banked, any task needing
  the crane queues behind the inner vessel's crane needs, and the
  transfer distance/handling steps add the +15–25% (double-banked) or
  +30–50% (triple-banked) service-time multiplier described in the
  Arena scenario file.
- **Repair berth** capacity (2) is what limits how many vessels can have
  their non-dock work (T11, T12) running in parallel with another
  vessel's dock occupancy — if you're testing more than 2 vessels in
  the yard at once (Arena Scenario 1), this becomes a second queue
  point worth tracking alongside dock occupancy.
- Fill in actual headcounts where this file says "specify from your
  yard" — these are placeholders sized for a Panamax-scale job, not
  numbers you should publish as fact.
