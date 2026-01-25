---
title: Sales Dashboards & Metrics
impact: HIGH
tags: dashboard, metrics, reporting, analytics, visualization
---

## Sales Dashboards & Metrics

**Impact: HIGH**

A great dashboard answers questions before they're asked. It drives behavior, not just measurement.

### Dashboard Design Hierarchy

```
┌─────────────────────────────────────────────────────────────┐
│                    EXECUTIVE DASHBOARD                       │
│   Monthly/Quarterly • Revenue, ARR, Pipeline, Forecast      │
│   Audience: C-suite, Board                                  │
├─────────────────────────────────────────────────────────────┤
│                    MANAGEMENT DASHBOARD                      │
│   Weekly • Team performance, Pipeline health, Forecast      │
│   Audience: VPs, Directors                                  │
├─────────────────────────────────────────────────────────────┤
│                    TEAM DASHBOARD                            │
│   Daily • Activity metrics, Open opps, Tasks due            │
│   Audience: Managers, Team leads                            │
├─────────────────────────────────────────────────────────────┤
│                    REP DASHBOARD                             │
│   Real-time • My pipeline, My quota, My activities          │
│   Audience: Individual reps                                 │
└─────────────────────────────────────────────────────────────┘
```

### Key Metrics by Role

| Role | Primary Metrics | Secondary Metrics |
|------|-----------------|-------------------|
| **SDR/BDR** | Meetings booked, Qualified opps | Activities, Response rate, Show rate |
| **AE** | Revenue closed, Pipeline created | Win rate, Avg deal size, Cycle time |
| **AM/CSM** | NRR, Expansion revenue | Churn rate, NPS, Health score |
| **Manager** | Team quota attainment | Rep performance distribution |
| **VP Sales** | Total revenue, Forecast accuracy | Pipeline coverage, Rep productivity |
| **CRO** | ARR growth, CAC payback | LTV:CAC, Sales efficiency |

### Dashboard Layout Best Practices

**Good Layout:**
```
┌─────────────────────────────────────────────────────────┐
│  HEADLINE METRICS (KPIs - big numbers)                  │
│  ┌──────┐  ┌──────┐  ┌──────┐  ┌──────┐               │
│  │$1.2M │  │ 78%  │  │ $45K │  │ 3.2x │               │
│  │Closed│  │ Quota│  │ ADS  │  │Cover │               │
│  └──────┘  └──────┘  └──────┘  └──────┘               │
├─────────────────────────────────────────────────────────┤
│  TREND CHARTS (left)    │   PIPELINE VISUAL (right)    │
│  ┌───────────────────┐  │   ┌───────────────────────┐  │
│  │ Revenue vs Quota  │  │   │   Pipeline by Stage   │  │
│  │     ~~~/~~~       │  │   │   █████████           │  │
│  │    /     \        │  │   │   ██████              │  │
│  └───────────────────┘  │   │   ████                │  │
│                         │   └───────────────────────┘  │
├─────────────────────────────────────────────────────────┤
│  ACTION ITEMS (tables/lists requiring attention)        │
│  • Opps closing this week: 12                          │
│  • Stale opps (>30 days): 8                            │
│  • Opps without next step: 5                           │
└─────────────────────────────────────────────────────────┘
```

**Bad Layout:**
```
┌─────────────────────────────────────────────────────────┐
│ [random chart] [random chart] [random chart]            │
│ [random chart] [random chart] [random chart]            │
│ [random chart] [random chart] [random chart]            │
│ [random chart] [random chart] [random chart]            │
│ (12 charts with no hierarchy or flow)                   │
└─────────────────────────────────────────────────────────┘
```

### Metric Definitions (Standardized)

| Metric | Definition | Formula |
|--------|------------|---------|
| **Quota Attainment** | % of quota achieved | Closed Won ÷ Quota × 100 |
| **Win Rate** | % of opps that close won | Closed Won ÷ (Closed Won + Closed Lost) × 100 |
| **Avg Deal Size (ADS)** | Average revenue per closed deal | Total Revenue ÷ # Closed Won Deals |
| **Sales Cycle** | Days from opp creation to close | Avg(Close Date - Created Date) |
| **Pipeline Coverage** | Multiple of quota in pipeline | Open Pipeline ÷ Remaining Quota |
| **Activity Rate** | Activities per rep per day | Total Activities ÷ Reps ÷ Working Days |
| **Conversion Rate** | % moving between stages | Stage N+1 Entries ÷ Stage N Entries |

### Visualization Best Practices

| Data Type | Best Visualization | Avoid |
|-----------|-------------------|-------|
| Single number (KPI) | Big number with trend arrow | Gauge charts |
| Trend over time | Line chart | 3D charts |
| Part-to-whole | Donut chart, stacked bar | Pie charts (>5 segments) |
| Comparison | Bar chart | Line chart for discrete values |
| Pipeline stages | Funnel or horizontal bar | Pie chart |
| Geographic | Map | Tables for >5 regions |
| Ranking | Sorted bar chart, table | Unsorted visualizations |

### Red Flag Indicators

Build alerts for these conditions:

| Condition | Threshold | Action |
|-----------|-----------|--------|
| Pipeline coverage drops | <2.5x quota | Notify VP Sales |
| Win rate declines | >5% drop MoM | Investigate by segment |
| Opp aging | >30 days in stage | Auto-task to rep |
| Forecast miss risk | <80% of commit | Escalate to manager |
| Activity decline | <50% of target | Manager 1:1 required |

### Report vs Dashboard

| Use Reports For | Use Dashboards For |
|-----------------|-------------------|
| Detailed data exploration | At-a-glance health check |
| Export to Excel | Quick decision making |
| Ad-hoc questions | Recurring monitoring |
| Audit/compliance | Driving behavior |
| Exception lists | Performance tracking |

### Dashboard Refresh Cadence

| Dashboard Type | Refresh Rate | Reason |
|----------------|--------------|--------|
| Executive | Daily | Board prep, strategic decisions |
| Management | Every 4 hours | Team oversight |
| Rep | Real-time | Immediate action |
| Activity | Real-time | Track daily progress |
| Forecast | Weekly | Commit calls |

### Common Dashboard Mistakes

**Mistake: Vanity metrics front and center**
```
Bad:  Total emails sent: 50,000
Good: Email reply rate: 12% (↑2% MoM)
```

**Mistake: No comparison context**
```
Bad:  Revenue this month: $500K
Good: Revenue this month: $500K (92% of quota, ↑15% YoY)
```

**Mistake: Too many filters**
```
Bad:  Dashboard with 8 filter dropdowns
Good: Pre-built views: "My Team", "Enterprise", "This Quarter"
```

### Anti-Patterns

- **Dashboard sprawl** — 50 reports no one uses
- **Metric inconsistency** — "Win rate" means different things to different teams
- **Delayed data** — Dashboard shows yesterday's data for real-time decisions
- **No drill-down** — Can't click through to underlying records
- **Filter paralysis** — Too many filter options, no defaults
- **Colorblind-unfriendly** — Red/green only visualizations
- **No mobile view** — Unusable on phone during meetings
