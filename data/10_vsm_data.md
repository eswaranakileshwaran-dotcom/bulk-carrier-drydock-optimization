# VSM Data — Current State Value Stream Map (20-Year Special Survey)

File: `data/10_vsm_data.md`

This supersedes `04_vsm_data.md` (kept in the repo as the original 5-year
baseline, per the note added in `05_scope_update.md`). Data box values
below are pulled from `07_process_task_data.md` (durations),
`08_resource_data.md` (crew/shifts), and are structured the same way the
original VSM file was, so the two are easy to compare station-for-station.

## Current State VSM Data Boxes

| Station | C/T (hrs, low–high) | Setup (hrs) | Uptime % | Crew | Shifts | WIP Before Station | VA or NVA |
|---|---|---|---|---|---|---|---|
| Yard selection & spec finalization | 168–240 | 8 | 70% | 3 | 1×8hr | 0 | NVA (necessary) |
| Pre-dock ROV survey & material pre-order | 240–336 | 8 | 65% | 3 | 1×8hr | 0 | NVA (necessary) |
| Vessel arrival & docking | 24–48 | 4 | 95% | 14 | 1×12hr | 0 | VA |
| Hull wash & inspection | 24–48 | 4 | 80% | 10 | 1×12hr | 0 | VA |
| Steel renewal — tank top | 192–456 | 8 | 70% | Steel crew | 2×12hr | 0 | VA |
| Steel renewal — bulkhead | 144–312 | 8 | 70% | Steel crew | 2×12hr | Waits for tank top | VA |
| Steel renewal — double bottom tanks | 240–504 | 8 | 70% | Steel crew | 2×12hr | Waits for bulkhead | VA |
| UTM gauging & Class approval | 48–72 | 2 | 60% | Class surveyor | Ad hoc | Rolling, per steel block | NVA (waiting) |
| Blast underwater hull | 120–192 | 8 | 70% | 8–10 | 2×12hr | Waits for steel completion | VA |
| Recoat hull + boot top (5-yr cycle) | 96–144 | 4 | 80% | 8–10 | 2×12hr | Waits for blasting | VA |
| Main engine overhaul | 432–528 | 8 | 75% | 5–6 | 1×8hr | 0 (parallel) | VA |
| Auxiliary engine overhaul | 336–432 | 8 | 75% | 4 | 1×8hr | 0 (parallel) | VA |
| Auxiliary equipment overhaul | 360–480 | 8 | 65% | 4–5 | 1×8hr | 0 (parallel, can start at anchorage) | VA |
| Safety & fire-fighting equipment renewal | 192–288 | 4 | 65% | 2–3 | 1×8hr | 0 (parallel, repair berth) | VA |
| Class surveys — full certification | 48–72 | 2 | 60% | Class surveyor | Ad hoc | Waits for all work packages | NVA (waiting) |
| Sea trials & undocking | 24–48 | 2 | 95% | 8 | 1×12hr | Waits for survey clearance | VA |

---

## Timeline Summary (Current State — 20-Year Survey Scope)

| Category | Hours (low–high) | Days (low–high) |
|---|---|---|
| Total lead time (ship off-hire) | 576–1,272 | 24–53 |
| Value-added time (steel + coating critical path) | 576–1,272 | 24–53 |
| Non-value-added time (planning, surveyor waiting, class sign-off) | 264–360 | 11–15 |
| VA ratio (process efficiency) | ~55–60% (approx., varies with scenario) | — |

Note: unlike the original 5-year VSM (single fixed 30-day lead time), this
scope is deliberately expressed as a range, because the steel-renewal
duration is the yard-capacity-constrained variable (see
`01_case_study_definition.md`). Use the Arena model to convert this range
into a probability distribution rather than picking one number for the
"current state."

---

## Waste Identification (7 Wastes — Lean), 20-Year Scope

| Waste Type | Where It Occurs | Impact |
|---|---|---|
| **Waiting** | Crane queue between docked and banked vessels; surveyor attendance not pre-booked | 8–30 hrs per occurrence, worse under double/triple banking |
| **Defects / Rework** | Additional steel found during gauging beyond the 600–800 t estimate | 48–96 hrs added |
| **Overprocessing** | Blasting/coating area larger than the actual renewed-steel footprint | 8–16 hrs wasted |
| **Transport** | Spare parts (engine, aux equipment) delivered late to yard | 24–48 hrs delay |
| **Underutilized talent** | Steel crew on partial shifts when tonnage discovered is at the low end of the range | Idle capacity — schedule buffer wasted |
| **Inventory** | Steel plate not pre-cut/pre-ordered to the surveyed tonnage | 24–72 hrs expediting |
| **Excess motion/handling** | Equipment moved across double/triple-banked vessels — the criticality-of-movement issue driving Arena Scenario 3 | 15–50% time penalty on crane-dependent tasks |

---

## Push vs Pull Analysis

### Current State — Push System
- Steel renewal tonnage assumed at contract stage; actual gauging may
  reveal more, forcing a schedule extension
- Surveyor called reactively rather than pre-booked against the 20-year
  statutory milestone
- Crane allocated first-come-first-served across docked/banked vessels

### Future State — Pull System (Target)
- Pre-dock ROV survey (T02) narrows the 600–800 t estimate before
  docking, tightening the steel-duration range
- Surveyor attendance locked to the fixed 20-year statutory schedule
  at project start
- Non-dock work (T11, T12) pulled off the dry dock and routed to repair
  berth as standard practice, not an exception
- Crane priority rules defined in advance for banked-vessel scenarios,
  rather than negotiated in real time

---

## Takt Time Calculation

Available dock time = target dock window (set this from your contract —
the low end of the steel range, ~24 days, is the aggressive target;
53 days is the capacity-constrained ceiling).

Customer demand unit = 1 statutory certificate required for the 20-year
Special Survey (hull, propeller/shaft, main engine, boiler, load line,
safety equipment, MARPOL — same 7-certificate structure as the original
VSM, since these are class-mandated regardless of survey type).

**Takt time = available dock days × 24 hrs ÷ 7 certificates**

At the aggressive 24-day target: 576 hrs ÷ 7 ≈ **82 hours/certificate**
At the 53-day ceiling: 1,272 hrs ÷ 7 ≈ **182 hours/certificate**

Phases likely exceeding the aggressive takt (82 hrs):
- Steel renewal (all three blocks) — capacity-constrained, will exceed
  takt except at the very low end of the tonnage range
- Main engine overhaul — 432+ hrs, well above takt, but runs in
  parallel so doesn't extend the dock stay by itself

Same limitation note as the original VSM applies: takt time here is a
directional benchmarking tool for a project-based (not repetitive)
process, not a precise production target.

---

## Data Sources & References

| # | Source | Used For |
|---|---|---|
| 1 | `07_process_task_data.md` | Task durations, predecessors |
| 2 | `08_resource_data.md` | Crew sizes, shift patterns, steel crew capacity |
| 3 | `09_cost_data.md` | Cost basis (not reproduced in this file — see cost file directly) |
| 4 | Dev & Saha (2015) — Ship Repairing Time Study | Cycle time benchmarks, uptime estimates (carried over from original VSM) |
