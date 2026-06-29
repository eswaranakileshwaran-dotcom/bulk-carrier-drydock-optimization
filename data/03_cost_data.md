# Cost Data — Bulk Carrier Dry Dock

## Purpose
This file documents all cost data used in the project — dock costs,
off-hire revenue loss, task-level cost estimates, and shipyard location
comparison. All figures in USD.

---

## Off-Hire Cost (Most Important Number in the Project)

Off-hire means the vessel is out of commercial service and earning nothing.
Every day in dry dock is a day of lost charter revenue PLUS direct repair costs.

| Vessel Type | Off-hire Rate | Source |
|-------------|--------------|--------|
| Panamax bulk carrier (our vessel) | $15,000–$25,000/day | Quora maritime cost Q&A |
| Supramax bulk carrier | $10,000–$18,000/day | Industry benchmark |
| Capesize bulk carrier | $20,000–$35,000/day | Industry benchmark |

**Project baseline:** $20,000/day (midpoint for Panamax)

### Off-Hire Cost by Scenario

| Scenario | Dock Duration | Off-hire Days | Off-hire Cost | Saving vs Baseline |
|----------|--------------|---------------|--------------|-------------------|
| Baseline (current) | 30 days | 30 | $600,000 | — |
| Target (optimized) | 20 days | 20 | $400,000 | $200,000 |
| Best case | 18 days | 18 | $360,000 | $240,000 |

---

## Direct Dock Cost Breakdown (Panamax Bulk Carrier)

| Cost Category | Low Estimate | High Estimate | Notes |
|---------------|-------------|--------------|-------|
| Dock rental (graving dock) | $5,000/day | $15,000/day | Varies by yard location |
| Hull blasting & painting | $400,000 | $800,000 | Material + labor combined |
| Main engine overhaul | $150,000 | $400,000 | Depends on scope |
| Propeller & shaft work | $80,000 | $200,000 | Including alignment |
| Steel renewal | $2,000/tonne | $5,000/tonne | If required |
| Class survey fees | $20,000 | $60,000 | All surveys combined |
| Temporary services | $10,000 | $30,000 | Shore power, water, waste |
| **Total direct cost** | **$700,000** | **$1,600,000** | Excludes off-hire |
| **Total all-in cost** | **$1,300,000** | **$2,200,000** | Includes off-hire at $20K/day |

---

## Cost of Delay (Why Bottlenecks Are Expensive)

Every unplanned day caused by a bottleneck costs:

| Cost Component | Per Day |
|---------------|---------|
| Off-hire revenue loss | $20,000 |
| Additional dock rental | $10,000 |
| Crew wages (ship + yard) | $5,000 |
| **Total cost per unplanned day** | **$35,000** |

This is why the class surveyor delay (8–16 hrs average wait) and
crane contention are not minor inconveniences — each surveyor delay
event costs approximately $12,000–$23,000 in combined losses.

---

## Shipyard Location Comparison

Shipyard selection is a major strategic decision. Cheaper labor
doesn't always mean lower total cost — transit days add off-hire time.

| Location | Labor Cost | Quality | Transit Days (from Asia route) | Dock Rental | Best For |
|----------|-----------|---------|-------------------------------|------------|---------|
| China (Shanghai / Guangzhou) | Low | High | 0–3 | Low | Cost-sensitive, high volume |
| South Korea (Busan) | Medium-High | Very High | 0–2 | Medium | Quality-critical work |
| Singapore | High | Very High | 0–1 | High | Emergency or complex jobs |
| India (Mumbai) | Very Low | Medium | 3–7 | Very Low | Budget dockings |
| Turkey (Tuzla) | Medium | High | 10–15 | Medium | Mediterranean-route vessels |
| UAE (Dubai) | Medium-High | High | 5–8 | Medium-High | Middle East route vessels |
| Europe (Rotterdam) | Very High | Very High | 15–20 | Very High | Regulatory or warranty work |

### Transit Cost Penalty
Transit days = additional off-hire at $20,000/day.

| Yard Location | Extra Transit Days vs Singapore | Extra Off-hire Cost |
|--------------|--------------------------------|-------------------|
| Singapore | 0 | $0 |
| China | 1–3 | $20,000–$60,000 |
| India | 4–7 | $80,000–$140,000 |
| Turkey | 10–15 | $200,000–$300,000 |
| Europe | 15–20 | $300,000–$400,000 |

> Key insight: A yard offering $200,000 cheaper repairs but located
> 10 transit days away may actually cost MORE in total when off-hire
> is factored in. This is a core finding to model in the project.

---

## Data Sources & References

| # | Source | Used For |
|---|--------|---------|
| 1 | [Quora — Dry Dock Cost Breakdown](https://www.quora.com/How-much-does-dry-docking-a-ship-for-repairs-cost-What-are-the-costs-involved) | Direct cost ranges by category, off-hire rates |
| 2 | [Marine Inspection — Dry Dock Preparation](https://marineinspection.app/blog/dry-dock-preparation-united-states) | Delay costs $35,000–$75,000/day, planning impact on cost |
| 3 | [Nautilus Shipping — Dry Dock Planning Guide](https://www.nautilusshipping.com/news-and-insights/dry-dock-planning-a-practical-guide-for-safer-smarter-vessel-maintenance-for-maritime-operations) | Routine vs extended dock duration and cost drivers |
| 4 | [Heisenberg Shipping — Dry Docking Guide](https://heisenbergshipping.com/dry-docking/) | Shipyard location factors, graving dock characteristics |
| 5 | [OUCO Industry — Dry Dock Guide](https://ouco-industry.com/what-is-a-dry-dock-8-things-you-need-to-know/) | Cargo ship docking intervals, cost factors by vessel type |
