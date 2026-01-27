---
title: Workforce Management & Capacity Planning
impact: MEDIUM-HIGH
tags: workforce, capacity, scheduling, forecasting, staffing, utilization
---

## Workforce Management & Capacity Planning

**Impact: MEDIUM-HIGH**

Right-sizing your support team is a constant balancing act. Too few agents and customers wait too long. Too many and you're burning budget. Workforce management turns ticket volume into staffing decisions.

### The Capacity Planning Equation

```
                    Ticket Volume × Handle Time
Required Agents = ─────────────────────────────────────
                   Available Hours × Utilization Rate

Example:
    500 tickets/day × 20 min/ticket = 10,000 minutes
    8 hours × 60 min × 75% utilization = 360 min/agent/day
    10,000 ÷ 360 = 28 agents needed
```

### Capacity Variables

| Variable | Definition | How to Get |
|----------|------------|------------|
| **Ticket Volume** | Tickets per time period | Historical data, forecasting |
| **Handle Time** | Avg time to resolve | Ticket analytics |
| **Available Hours** | Hours worked per agent | Schedules, less meetings |
| **Utilization Rate** | % time on tickets | Target 70-80% |
| **Shrinkage** | Non-productive time | Training, breaks, meetings |

### Utilization Breakdown

| Activity | Target % | Notes |
|----------|----------|-------|
| **Ticket handling** | 70-80% | Core productive time |
| **Training** | 5-10% | Ongoing development |
| **Meetings** | 5-8% | Team, 1:1s, calibration |
| **Admin** | 3-5% | Documentation, projects |
| **Breaks/Buffer** | 5-10% | Bathroom, mental breaks |
| **Shrinkage total** | 20-30% | Not available for tickets |

### Good Workforce Planning

```
✓ Data-driven forecasting
  → Historical patterns analyzed
  → Seasonality accounted for
  → Growth factored in

✓ Flexible staffing
  → Part-time for peak hours
  → Cross-trained backups
  → Contractor buffer available

✓ Real-time monitoring
  → Queue visibility
  → Quick response to spikes
  → Adjust on the fly

✓ Forward-looking
  → 3-month rolling forecast
  → Hiring lead time included
  → Training time planned

✓ Agent wellbeing
  → Sustainable utilization
  → Predictable schedules
  → Burnout prevention
```

### Bad Workforce Planning

```
✗ Reactive staffing
  → Hire after crisis
  → Always behind

✗ One-size schedules
  → Same coverage all hours
  → Peaks understaffed

✗ 100% utilization target
  → No buffer for spikes
  → Agent burnout

✗ Ignoring seasonality
  → January staff for December volume
  → Surprised every year

✗ Training as afterthought
  → New hires unproductive for months
  → Existing team can't grow
```

### Forecasting Methods

| Method | Description | Best For |
|--------|-------------|----------|
| **Historical average** | Last N periods average | Stable volume |
| **Trend analysis** | Apply growth rate | Growing companies |
| **Seasonal adjustment** | Last year same period | Clear seasonality |
| **Moving average** | Rolling X-week average | Smoothing noise |
| **Regression** | Volume vs drivers | Complex patterns |

### Seasonal Patterns to Watch

| Pattern | When | Planning Action |
|---------|------|-----------------|
| **Holiday dips** | Dec 24-Jan 1 | Reduced staffing OK |
| **End of month** | Last 3 days | Billing questions spike |
| **Monday surge** | Monday AM | Full staffing |
| **Release spikes** | After deployments | Extra staffing |
| **Renewal periods** | Quarterly | CS/billing tickets up |
| **Tax season** | April (US) | Financial software surge |

### Staffing Model by Channel

| Channel | Agent:Tickets/Hour | Concurrency | Notes |
|---------|-------------------|-------------|-------|
| **Email** | 4-8 | 1 | Deep work, can batch |
| **Live Chat** | 2-4 | 2-3 | Multiple simultaneous |
| **Phone** | 3-5 | 1 | No multitasking |
| **Social** | 5-10 | 1-2 | Often quick responses |

### Scheduling Best Practices

```
Schedule Design:
├── Cover peak hours with full staff
├── Stagger start times for coverage
├── Allow schedule preferences within limits
├── Plan for timezone coverage
└── Build in overlap for handoffs

Shift Examples:
├── Early: 6am-2pm (catch Asia-Pacific overlap)
├── Core: 9am-5pm (highest volume)
├── Late: 12pm-8pm (West Coast coverage)
└── Split: 9-1pm + 4-8pm (two peaks)
```

### Schedule Template

| Day | Early (6a-2p) | Core (9a-5p) | Late (12p-8p) | Total |
|-----|---------------|--------------|---------------|-------|
| Monday | 4 agents | 12 agents | 6 agents | 22 |
| Tuesday | 3 agents | 10 agents | 5 agents | 18 |
| Wednesday | 3 agents | 10 agents | 5 agents | 18 |
| Thursday | 3 agents | 10 agents | 5 agents | 18 |
| Friday | 3 agents | 8 agents | 4 agents | 15 |
| Saturday | 1 agent | 2 agents | 1 agent | 4 |
| Sunday | 1 agent | 2 agents | 1 agent | 4 |

### Real-Time Management

| Metric | Green | Yellow | Red | Action |
|--------|-------|--------|-----|--------|
| **Wait Time** | <5 min | 5-15 min | >15 min | Pull from training, escalate |
| **Queue Depth** | <10 | 10-25 | >25 | All hands, defer non-critical |
| **Utilization** | 70-80% | 80-90% | >90% | Monitor burnout, get help |
| **Available Agents** | Per plan | -2 | -4+ | Call in backups |

### Hiring Planning

| Scenario | Lead Time | Considerations |
|----------|-----------|----------------|
| **Replacement** | 2-3 months | Notice, interview, training |
| **Growth hire** | 3-4 months | Same + slower pipeline |
| **New tier/specialty** | 4-6 months | Harder to find, more training |
| **Seasonal** | 1-2 months | Temp/contract can be faster |

### New Hire Ramp Schedule

| Week | Focus | Ticket Load | Support |
|------|-------|-------------|---------|
| 1 | Orientation, product training | 0% | Classroom |
| 2 | Shadowing | 0% | Paired with mentor |
| 3 | Supervised tickets | 25% | QA every ticket |
| 4 | Supervised tickets | 50% | QA every ticket |
| 5-6 | Increasing independence | 75% | Daily check-ins |
| 7-8 | Full load | 100% | Standard support |

### Capacity Dashboard

| Metric | How to Calculate | Review |
|--------|------------------|--------|
| **Tickets/Agent/Day** | Total tickets ÷ FTE | Daily |
| **Handle Time Trend** | Avg over time | Weekly |
| **Utilization** | Ticket time ÷ Available time | Daily |
| **Backlog** | Tickets >24h old | Real-time |
| **Coverage Gaps** | Hours with <50% target staffing | Weekly |
| **Cost Per Ticket** | Support cost ÷ Total tickets | Monthly |

### Cost Per Ticket Analysis

```
Full Cost Calculation:
─────────────────────
Agent salary/benefits:     $60,000/year
Tools/systems (per seat):   $5,000/year
Training/development:       $2,000/year
Management overhead:        $8,000/year
Total per agent:          $75,000/year

Tickets per agent/year: 6,000 (25/day × 240 days)

Cost per ticket: $12.50

Reducing handle time by 10% = $1.25/ticket savings
Improving FCR by 5% = 300 tickets avoided = $3,750/agent/year
```

### Capacity Planning Calendar

```
Monthly:
□ Review previous month actuals vs forecast
□ Update 3-month rolling forecast
□ Adjust schedules for known events
□ Review hiring pipeline status

Quarterly:
□ Deep analysis of volume trends
□ Headcount planning for next 2 quarters
□ Training calendar planning
□ Budget review

Annually:
□ Annual volume forecast
□ Headcount budget request
□ Tool/vendor contract reviews
□ Strategic capacity planning
```

### Scenario Planning

| Scenario | Volume Change | Response |
|----------|---------------|----------|
| **Product outage** | +300% | All hands, defer non-critical |
| **Major release** | +50% | Pre-scheduled extra coverage |
| **Competitor migration** | +100% | Temp staff, extended hours |
| **Holiday** | -50% | Reduced staffing, skeleton crew |
| **PR crisis** | +500% | Emergency protocol, exec support |

### Anti-Patterns

- **Heroic unsustainable effort** — Team working overtime constantly
- **Understaffed normal** — Always behind, never catching up
- **Over-hiring for peak** — Paying for capacity used 10% of time
- **Ignoring ramp time** — New hires counted as full capacity
- **Static schedules** — Same coverage regardless of patterns
- **Utilization obsession** — 95% target burns out team
- **No forecast review** — Never learning from actuals
- **Last-minute scramble** — Emergency scheduling constantly
