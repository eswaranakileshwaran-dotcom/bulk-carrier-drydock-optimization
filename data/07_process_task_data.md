# Process Task Data — 20-Year Special Survey (Revised Scope)
Purpose: this is the task-level source data. `10_vsm_data.md` aggregates
these into VSM data boxes; the Gantt chart and Arena model both read
durations and predecessors from this table rather than restating them.

## Task list

| ID | Task | Location | Duration (days, low–high) | Predecessor | Crew (from 08) | Critical? |
|---|---|---|---|---|---|---|
| T01 | Yard selection & spec finalization | Office | 7–10 | — | Planning | No |
| T02 | Pre-dock ROV hull survey & material pre-order | Afloat (owner's port) | 10–14 | T01 | Planning | No |
| T03 | Vessel arrival & docking | Dry dock | 1–2 | T02 | Dock crew | Yes |
| T04 | Hull wash & inspection | Dry dock | 1–2 | T03 | Dock crew | Yes |
| T05a | Steel renewal — tank top plating | Dry dock | 8–19 | T04 | Steel crew | Yes |
| T05b | Steel renewal — bulkhead | Dry dock | 6–13 | T05a | Steel crew | Yes |
| T05c | Steel renewal — double bottom tanks | Dry dock | 10–21 | T05b | Steel crew | Yes |
| T06 | UTM gauging & Class approval of steel work | Dry dock | 2–3 | T05a (rolling, per block) | Class surveyor | Yes |
| T07 | Blast underwater hull | Dry dock | 5–8 | T05c | Blast/coat crew | Yes |
| T08 | Recoat hull + boot top (5-yr cycle) | Dry dock | 4–6 | T07 | Blast/coat crew | Yes |
| T09 | Main engine overhaul | Afloat/dock (parallel) | 18–22 | T03 | ME team | No (unless it overruns steel path) |
| T10 | Auxiliary engine overhaul | Afloat/dock (parallel) | 14–18 | T03 | AE team | No |
| T11 | Auxiliary equipment overhaul | Anchorage or repair berth (parallel) | 15–20 | Can start pre-docking | Aux equipment team | No |
| T12 | Safety & fire-fighting equipment renewal (20-yr) | Repair berth (parallel) | 8–12 | Can start pre-docking | Safety team | No |
| T13 | Class surveys — full certification | Dry dock or repair berth | 2–3 | T08, T09, T10, T11, T12 all complete | Class surveyor | Yes |
| T14 | Sea trials & undocking | Dry dock → sea | 1–2 | T13 | Dock crew | Yes |

## Notes

- T05a–T05c are shown sequential because they share one steel crew
  (capacity constraint, see `08_resource_data.md`); if two gangs are
  used instead, they can run partially in parallel — model both options
  in Arena rather than deciding here.
- T09–T12 are the tasks that can be pulled off the dry-dock critical
  path if routed to anchorage/repair berth — this is the direct input
  to Arena Scenario 4 (repair berth offload).
- Duration ranges came from tonnage ÷ yard capacity for T05a–T05c
  (see `01_case_study_definition.md`); the rest are placeholder ranges —
  replace with your yard's actual OEM overhaul durations once you have
  them.
