# VSM Data — Current State Value Stream Map

## Purpose
This file contains all data box values for the current state Value Stream Map.
Each row = one process station on the VSM. These numbers feed directly into
the Visio VSM drawing and the Arena DES model.

## What is a VSM Data Box?
In a Value Stream Map, every process station has a data box below it showing:
- **C/T** — Cycle Time: how long the process actually takes (hours)
- **Setup** — time to prepare before work starts (hours)
- **Uptime** — % of scheduled time the station is actually working
- **Crew** — number of workers at that station
- **Shifts** — how many shifts per day (1×8hr, 2×12hr etc.)
- **WIP** — work in progress waiting before this station (units — here, job packets)

---

## Current State VSM Data Boxes

| Station | C/T (hrs) | Setup (hrs) | Uptime % | Crew | Shifts | WIP Before Station | VA or NVA |
|---------|-----------|------------|---------|------|--------|-------------------|-----------|
| Pre-dock planning | 720 | 48 | 60% | 3 | 1×8hr | 0 | NVA (necessary) |
| Vessel arrival & docking | 31 | 4 | 95% | 16 | 1×12hr | 0 | VA |
| Hull wash & inspection | 24 | 4 | 80% | 10 | 1×12hr | 0 | VA |
| Grit blasting | 96 | 8 | 70% | 14 | 2×12hr | 0 | VA |
| Hull painting | 72 | 4 | 80% | 6 | 2×12hr | Waits for blasting | VA |
| Propeller & shaft | 72 | 4 | 85% | 4 | 1×12hr | 0 (parallel) | VA |
| Engine overhaul | 96 | 8 | 75% | 5 | 1×8hr | 0 (parallel) | VA |
| Tank inspection | 96 | 8 | 60% | 6 | 1×8hr | 0 (parallel) | VA |
| Class surveys | 36 | 2 | 60% | 2 | 1×8hr | Waits for work completion | NVA (waiting) |
| Sea trials & undocking | 27 | 2 | 95% | 8 | 1×12hr | Waits for survey clearance | VA |

---

## Timeline Summary (Current State)

| Category | Hours | Days |
|----------|-------|------|
| Total lead time (ship off-hire) | 720 | 30 |
| Value-added time | 336 | 14 |
| Non-value-added time | 384 | 16 |
| VA ratio (process efficiency) | 47% | — |

---

## Waste Identification (7 Wastes — Lean)

| Waste Type | Where It Occurs | Impact |
|-----------|----------------|--------|
| **Waiting** | Crane queue (Phase 2 vs 3), surveyor delays, material delivery | 8–24 hrs per occurrence |
| **Defects / Rework** | Unplanned steel found during blasting — restarts paint schedule | 48–72 hrs added |
| **Overprocessing** | Excess blasting beyond required area | 8–12 hrs wasted |
| **Transport** | Late spare parts delivery from procurement | 24–48 hrs delay |
| **Underutilized talent** | Engine techs on 1 shift only — idle 16 hrs/day | 36+ hrs lost on engine overhaul |
| **Inventory** | Materials not pre-ordered — reactive procurement | 24–48 hrs expediting |

---

## Push vs Pull Analysis

### Current State — Push System
- Tasks scheduled sequentially based on fixed plan
- Steel renewal discovered during inspection forces unplanned pause
- Surveyor scheduled reactively — called when work finishes, not pre-booked
- Crane allocated first-come first-served between Phase 2 and Phase 3

### Future State — Pull System (Target)
- Pre-dock ROV hull survey identifies steel renewal areas 2 months early
- Materials pre-ordered and staged before vessel arrives
- Surveyor attendance locked to fixed schedule at project start
- Crane dedicated to Phase 3 during days 1–10, Phase 2 steel work scheduled around it
- Engine overhaul moved to 2-shift operation

---

## Future State Target Data Boxes

| Station | Current C/T (hrs) | Target C/T (hrs) | Improvement Method |
|---------|------------------|-----------------|-------------------|
| Grit blasting | 96 | 96 | No change — equipment limited |
| Hull painting | 72 | 72 | No change — follows blasting |
| Propeller & shaft | 72 | 60 | Dedicated crane — no queuing |
| Engine overhaul | 96 | 60 | 2-shift operation |
| Class surveys | 36 | 36 | No change in survey time |
| Surveyor waiting | 16 (avg) | 2 | Pre-scheduled attendance |
| Steel rework delay | 60 (avg) | 8 | Pre-dock ROV survey |
| **Total lead time** | **720 hrs** | **480 hrs** | **33% reduction** |

---

## Takt Time Calculation

Takt time = available time / customer demand rate

Definitions for this project:
- Available dock time = 504 hrs (21 days — contracted target window)
- Customer demand unit = 1 class survey certificate
- Number of certificates required = 7 (hull, propeller/shaft, main engine,
  boiler, load line, safety equipment, MARPOL)
- Rationale: survey certificates are the externally mandated deliverables
  the ship owner and classification society require before the vessel
  can legally return to service. They are discrete, equal-weight outputs
  that drive the entire dock schedule.

**Takt Time = 504 hrs / 7 certificates = 72 hours per certificate**

This means the process must deliver one survey-ready work package
every 72 hours to meet the 21-day target.

Phases currently exceeding 72-hour takt:
- Grit blasting: 96 hrs ❌ — equipment constrained (blast machines)
- Engine overhaul: 96 hrs ❌ — shift constrained (1 shift only)
- Tank inspection: 96 hrs ❌ — crew constrained (confined space rules)

> Limitation: Takt time is most precise in repetitive manufacturing
> where each unit is identical. In dry dock — a project environment —
> survey certificates vary in complexity and duration (4–12 hrs each).
> Takt time is therefore used here as a directional benchmarking tool
> to identify over-consuming phases, not as a precise production target.
> This limitation is acknowledged per lean literature on project-based
> environments (Womack & Jones, Lean Thinking, 1996).

---

## Data Sources & References

| # | Source | Used For |
|---|--------|---------|
| 1 | [Dev & Saha (2015) — Ship Repairing Time Study](https://scispace.com/pdf/dry-docking-time-and-labour-46slnefmiw.pdf) | Cycle time benchmarks, uptime estimates |
| 2 |
