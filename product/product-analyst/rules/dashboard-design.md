---
title: Dashboard Design for Product
impact: MEDIUM-HIGH
tags: dashboard, visualization, reporting, self-serve
---

## Dashboard Design for Product

**Impact: MEDIUM-HIGH**

The best dashboards drive action, not just awareness. Design dashboards that answer questions and prompt decisions.

### Dashboard Design Principles

**1. One Dashboard, One Purpose**
```
Bad: "Product Dashboard" (everything)
Good: "Weekly Activation Health Check" (specific purpose)
```

**2. Action-Oriented**
```
Ask: "What will someone DO after viewing this?"
If no clear action → wrong metrics or wrong audience
```

**3. Audience-Appropriate**
```
Executive: High-level trends, strategic metrics
Manager: Team performance, weekly progress
IC: Detailed diagnostics, debugging tools
```

**4. Progressive Disclosure**
```
Level 1: Summary metrics (5 seconds to understand)
Level 2: Key trends (30 seconds)
Level 3: Segment breakdowns (2 minutes)
Level 4: Detailed drill-down (investigation)
```

### Dashboard Architecture

**The Dashboard Hierarchy:**

```
                    ┌─────────────────────┐
                    │    Executive        │  Weekly/Monthly
                    │    Overview         │  Strategy decisions
                    └──────────┬──────────┘
                               │
            ┌──────────────────┼──────────────────┐
            ▼                  ▼                  ▼
    ┌───────────────┐  ┌───────────────┐  ┌───────────────┐
    │   Growth      │  │   Product     │  │   Revenue     │
    │   Dashboard   │  │   Health      │  │   Metrics     │
    └───────┬───────┘  └───────┬───────┘  └───────┬───────┘
            │                  │                  │
    ┌───────┴───────┐  ┌───────┴───────┐  ┌───────┴───────┐
    │  Acquisition  │  │  Retention    │  │  Conversion   │
    │  Activation   │  │  Engagement   │  │  Expansion    │
    │  Funnel       │  │  Feature      │  │  Churn        │
    └───────────────┘  └───────────────┘  └───────────────┘
            │                  │                  │
            ▼                  ▼                  ▼
    [Detailed drill-down dashboards and ad-hoc exploration]
```

### Dashboard Types and Templates

**1. Executive Overview**

| Section | Metrics | Visualization |
|---------|---------|---------------|
| **Health Score** | Overall product score (composite) | Single number + trend |
| **North Star** | Primary metric + trend | Big number + sparkline |
| **AARRR Summary** | Each stage's key metric | Row of metrics |
| **Risks/Wins** | Notable changes this period | Text callouts |

**Layout:**
```
┌────────────────────────────────────────────────────────┐
│  PRODUCT HEALTH SCORE: 78/100 (↑3 vs last week)       │
├────────────────────────────────────────────────────────┤
│  ┌──────────┐ ┌──────────┐ ┌──────────┐ ┌──────────┐  │
│  │ SIGNUPS  │ │ACTIVATION│ │RETENTION │ │ REVENUE  │  │
│  │  2,340   │ │   62%    │ │   45%    │ │  $142K   │  │
│  │  +12%    │ │   +3pp   │ │   -1pp   │ │   +8%    │  │
│  └──────────┘ └──────────┘ └──────────┘ └──────────┘  │
├────────────────────────────────────────────────────────┤
│  📈 Wins: Activation hit all-time high                │
│  ⚠️ Watch: D30 retention declining for 3 weeks       │
└────────────────────────────────────────────────────────┘
```

**2. Funnel Dashboard**

```
┌────────────────────────────────────────────────────────┐
│               SIGNUP FUNNEL (Last 7 Days)              │
├────────────────────────────────────────────────────────┤
│                                                        │
│  Landing Page   ██████████████████████████  10,000     │
│                              ↓ 35%                     │
│  Started Signup ████████████                 3,500     │
│                              ↓ 78%                     │
│  Completed      ████████                     2,730     │
│                              ↓ 52%                     │
│  Activated      █████                        1,420     │
│                              ↓ 35%                     │
│  Retained (D7)  ██                            497      │
│                                                        │
├────────────────────────────────────────────────────────┤
│  Biggest drop-off: Completed → Activated (48% loss)   │
│  vs Last Week: Start→Complete improved +5pp          │
└────────────────────────────────────────────────────────┘
```

**3. Retention Dashboard**

```
┌────────────────────────────────────────────────────────┐
│              RETENTION COHORT ANALYSIS                 │
├────────────────────────────────────────────────────────┤
│         │ W0   │ W1   │ W2   │ W3   │ W4   │ W5      │
│  Jan 1  │ 100% │ 45%  │ 38%  │ 32%  │ 29%  │ 28%     │
│  Jan 8  │ 100% │ 47%  │ 40%  │ 35%  │ 31%  │         │
│  Jan 15 │ 100% │ 48%  │ 42%  │ 38%  │      │         │
│  Jan 22 │ 100% │ 52%  │ 45%  │      │      │         │
├────────────────────────────────────────────────────────┤
│  Trend: W1 retention improving (45% → 52%)            │
│  Target: 55% W1 by end of Q1                          │
└────────────────────────────────────────────────────────┘
```

**4. Feature Adoption Dashboard**

```
┌────────────────────────────────────────────────────────┐
│              FEATURE ADOPTION TRACKER                  │
├────────────────────────────────────────────────────────┤
│  Feature            │ Adoption │ Trend │ Health       │
│  ─────────────────────────────────────────────────────│
│  Core Reporting     │   72%    │  ↑    │ ✅ Strong    │
│  Collaboration      │   48%    │  ↑    │ ✅ Growing   │
│  Advanced Analytics │   25%    │  →    │ ⚠️ Stalled  │
│  API Access         │   12%    │  ↓    │ ⚠️ Watch    │
│  New: Smart Alerts  │    8%    │  ↑    │ 🆕 Ramping  │
├────────────────────────────────────────────────────────┤
│  Focus Area: Advanced Analytics discovery             │
└────────────────────────────────────────────────────────┘
```

### Visualization Best Practices

**Choose the Right Chart:**

| Data Type | Best Visualization | Avoid |
|-----------|-------------------|-------|
| **Single metric** | Big number, gauge | Pie chart |
| **Trend over time** | Line chart | Stacked bar |
| **Part of whole** | Stacked bar, 100% bar | Pie chart (>5 segments) |
| **Comparison** | Horizontal bar | Vertical bar (many items) |
| **Distribution** | Histogram, box plot | Pie chart |
| **Correlation** | Scatter plot | Line chart |
| **Funnel** | Funnel chart, waterfall | Pie chart |

**Color Usage:**

```
Use color intentionally:
- Green: Good/positive/target met
- Red: Bad/negative/needs attention
- Yellow: Warning/watch
- Gray: Neutral/context
- Blue: Primary data series

Avoid:
- Rainbow charts
- More than 5 colors
- Red/green only (colorblind users)
```

### Good vs Bad Dashboard Examples

**Good: Focused, Actionable**
```
Dashboard: Weekly Activation Review
Audience: Growth team
Purpose: Identify activation blockers

Content:
1. Activation rate vs target (big number)
2. Activation funnel with WoW comparison
3. Top 3 drop-off points with absolute numbers
4. Cohort activation trend (are we improving?)
5. Segment breakdown (mobile vs web, source)

Actions enabled:
- Identify biggest activation blocker
- Prioritize next optimization
- Track experiment impact
```

**Bad: Unfocused, Vanity-Driven**
```
Dashboard: Product Dashboard
Audience: Everyone
Purpose: Show everything

Content:
1. Total users (all-time, always up!)
2. Page views (meaningless)
3. Session duration (average, not segmented)
4. 47 different charts
5. No trends or comparisons

Problems:
- No clear purpose
- Vanity metrics
- Too much information
- No actionable insight
- Wrong granularity
```

### Self-Serve Analytics

**Building Self-Serve Culture:**

| Level | What Users Can Do | Tools |
|-------|------------------|-------|
| **Viewer** | See pre-built dashboards | Dashboard tool |
| **Explorer** | Filter, segment, drill-down | BI tool |
| **Builder** | Create simple charts | BI tool |
| **Analyst** | Write SQL, complex analysis | SQL tool |

**Self-Serve Guardrails:**

```
✓ Do:
- Provide data dictionary
- Offer templates and examples
- Set up calculated metrics
- Enable sandboxed exploration

✗ Don't:
- Give raw database access
- Allow editing production dashboards
- Let users create without naming conventions
```

### Dashboard Maintenance

**Review Cadence:**

| Activity | Frequency |
|----------|-----------|
| **Metric accuracy check** | Weekly |
| **Usage review** | Monthly |
| **Relevance audit** | Quarterly |
| **Full dashboard review** | Semi-annually |

**Health Indicators:**

| Signal | Healthy | Unhealthy |
|--------|---------|-----------|
| **Views/week** | >10 | <3 |
| **Active explorers** | Growing | Declining |
| **Stale dashboards** | <10% | >30% |
| **User questions** | Decreasing | Increasing |

### Anti-Patterns

- **Dashboard sprawl** — 50 dashboards, nobody uses any
- **Vanity metrics** — Always-up numbers that don't drive action
- **No context** — Numbers without targets, trends, or comparisons
- **Information overload** — 30 charts on one page
- **Stale data** — Data from yesterday (or last week)
- **No ownership** — Nobody maintains, data quality degrades
- **Pretty but useless** — Beautiful charts with no insight
- **One-size-fits-all** — Same dashboard for exec and IC
