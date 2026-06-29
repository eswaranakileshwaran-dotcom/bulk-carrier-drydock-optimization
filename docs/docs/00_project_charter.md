# Project Charter — Bulk Carrier Dry Dock Optimization

## Problem Statement
A Panamax bulk carrier (~75,000 DWT) undergoing its mandatory 5-year Special
Survey dry dock spends an average of 25–35 days off-hire. At $15,000–$25,000
per off-hire day, poor planning and execution inflate costs by $300K–$750K per
docking cycle compared to a well-optimized baseline. The root causes are
unresolved: shared resource bottlenecks, sequential scheduling of parallelizable
tasks, reactive material procurement, and uncoordinated class society surveyor
attendance.

## Project Objective
Identify, quantify, and validate process improvements that reduce total dock
time by 30–40% (target: 18–22 days) using lean process mapping and discrete
event simulation.

## Vessel Scope
| Parameter | Value |
|-----------|-------|
| Vessel type | Panamax Bulk Carrier |
| Deadweight tonnage | ~75,000 DWT |
| Length overall | ~225 m |
| Dry dock trigger | 5-year Special Survey (IMO / Class requirement) |
| Intermediate survey | 2.5-year (out-of-dock) |
| Dock type modeled | Graving dock |

## Methodology
1. Data collection and literature review
2. Swim lane process map (draw.io)
3. Value Stream Map — current state (Visio)
4. Arena Discrete Event Simulation — baseline model
5. Bottleneck analysis from simulation output
6. Scenario analysis — 5 improvement scenarios in Arena
7. Value Stream Map — future state (Visio)
8. Results documentation and GitHub publishing

## Tools
| Tool | Purpose |
|------|---------|
| draw.io | Swim lane / BPMN process map |
| Microsoft Visio | Value Stream Map (current + future state) |
| Arena Simulation 16 | Discrete Event Simulation model |
| GitHub | Version control and project documentation |
| Excel | Data tables, output analysis |

## Key Metrics
- Total dock duration (days)
- Value-added time vs non-value-added time (VA ratio %)
- Resource utilization % per bottleneck resource
- Cost per docking cycle ($)
- Off-hire days saved per scenario

## Author
# Akileshwaran Eswaran
# USC Industrial & Systems Engineering Graduate
# Portfolio project — 2026
