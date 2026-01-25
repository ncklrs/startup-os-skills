---
title: Usage Analytics & Adoption Metrics
impact: HIGH
tags: usage-analytics, adoption-metrics, engagement, product-analytics
---

## Usage Analytics & Adoption Metrics

**Impact: HIGH**

Usage data is the most honest signal of customer health. Customers can tell you they're happy while silently disengaging — usage data tells the real story. Effective usage analytics separate healthy accounts from future churns 60-90 days in advance.

### The Usage Analytics Hierarchy

```
┌──────────────────────────────────────────────────────────────────┐
│                    USAGE ANALYTICS HIERARCHY                     │
├──────────────────────────────────────────────────────────────────┤
│                                                                  │
│  Level 1: ACTIVITY                                               │
│  └── Are they logging in?                                        │
│      Metrics: DAU, WAU, MAU, session count                       │
│                                                                  │
│  Level 2: ENGAGEMENT                                             │
│  └── What are they doing?                                        │
│      Metrics: Actions per session, time in app, feature usage    │
│                                                                  │
│  Level 3: ADOPTION                                               │
│  └── Are they using core features?                               │
│      Metrics: Feature adoption %, key workflow completion        │
│                                                                  │
│  Level 4: VALUE                                                  │
│  └── Are they achieving outcomes?                                │
│      Metrics: Goals completed, ROI realized, business impact     │
│                                                                  │
└──────────────────────────────────────────────────────────────────┘
```

### Key Usage Metrics

| Metric | Definition | Formula | Target |
|--------|------------|---------|--------|
| **DAU/MAU** | Stickiness ratio | Daily active / Monthly active | 25-40% |
| **L7/L30** | Weekly engagement | 7-day active / 30-day active | 40-60% |
| **Sessions/User/Week** | Usage frequency | Weekly sessions / Active users | 3-5+ |
| **Actions per Session** | Usage depth | Total actions / Sessions | 10-20+ |
| **Feature Adoption Rate** | Breadth | Features used / Available features | 40-60% |
| **Power User %** | Top engagement | Users >80th percentile / Total | 15-25% |
| **Dormant %** | Inactive accounts | No login 30+ days / Total | <10% |

### Feature Adoption Framework

```
Feature Classification:

CORE (Must Use)         EXPANSION (Growth)       ADVANCED (Power)
├── Essential to        ├── Multiplies value     ├── Differentiating
│   basic value         │                        │   capabilities
├── Onboarding focus    ├── Growth milestone     ├── Power user features
├── 100% adoption       ├── 40-60% adoption      ├── 15-25% adoption
│   target              │   target               │   target
│                       │                        │
Examples:               Examples:                Examples:
- CRM: Contact mgmt     - CRM: Automations       - CRM: Custom objects
- Analytics: Dashboards - Analytics: Alerts      - Analytics: API access
- Support: Tickets      - Support: Self-service  - Support: Integrations
```

### Good Usage Dashboard Design

```
Customer Usage Dashboard: Acme Corp

┌─────────────────────────────────────────────────────────────────┐
│  OVERALL HEALTH                                    Score: 72    │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  ACTIVITY METRICS (Last 30 Days)                               │
│  ├── Active Users:        45 of 60 licensed (75%)             │
│  ├── DAU/MAU:             28% (industry avg: 25%)             │
│  ├── Sessions/User/Week:  3.2 (↓ from 4.1 last month)         │
│  └── Trend:               ⚠ Declining (-22% MoM)              │
│                                                                 │
│  FEATURE ADOPTION                                               │
│  ├── Core Features:       ████████████████░░░░ 82%             │
│  ├── Expansion Features:  ████████████░░░░░░░░ 58%             │
│  └── Advanced Features:   ████░░░░░░░░░░░░░░░░ 21%             │
│                                                                 │
│  TOP FEATURES BY USAGE                                          │
│  1. Dashboard views       ████████████████████ 2,340           │
│  2. Report exports        ████████████████     1,856           │
│  3. Alert configuration   ████████████         1,247           │
│  4. Team collaboration    ████████             892             │
│  5. API calls             ██████               634             │
│                                                                 │
│  USER SEGMENTS                                                  │
│  ├── Power Users (5+/wk):    12 users (27%)                    │
│  ├── Regular (2-4/wk):       23 users (51%)                    │
│  ├── Light (1/wk):           7 users (16%)                     │
│  └── Dormant (0/wk):         3 users (7%)                      │
│                                                                 │
│  ⚠ ALERT: Usage declining 22% — recommend CSM outreach         │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### Bad Usage Dashboard Design

```
Usage Report: Acme Corp

Total Logins: 12,456
Total Actions: 89,234
Features Available: 47
Features Used: 31

Problems:
✗ All-time totals, not recent activity
✗ No trend information
✗ No context (vs. baseline, vs. peers)
✗ No user-level breakdown
✗ No actionable insights
✗ Missing dormant user identification
✗ No health score integration
```

### Usage Pattern Analysis

| Pattern | Definition | Health Signal | Action |
|---------|------------|---------------|--------|
| **Steady High** | Consistent strong usage | Healthy | Expansion |
| **Growing** | Increasing over time | Very Healthy | Case study |
| **Plateau** | Stable but not growing | Neutral | Feature adoption push |
| **Declining** | Decreasing over time | At Risk | Intervention |
| **Sporadic** | Inconsistent engagement | Warning | Usage training |
| **Concentrated** | Few power users | Risk | Broaden adoption |
| **Dormant** | No recent activity | Critical | Re-activation |

### User Segmentation by Usage

| Segment | Definition | % of Users | Strategy |
|---------|------------|------------|----------|
| **Champions** | Daily use, high depth, advocates | 10-15% | Expand, case studies |
| **Power Users** | Frequent use, feature breadth | 15-25% | Feature adoption |
| **Regular Users** | Consistent weekly use | 30-40% | Habit formation |
| **Casual Users** | Monthly, light use | 15-25% | Increase engagement |
| **At-Risk** | Declining usage | 10-15% | Re-engagement |
| **Dormant** | No use 30+ days | 5-10% | Reactivation |

### Adoption Milestone Tracking

```
Customer Journey: Feature Adoption Milestones

Day 1:  First Login                                    ✓
Day 3:  Complete profile setup                         ✓
Day 7:  Create first [core object]                     ✓
Day 14: Invite team member                             ✓
Day 21: Set up first automation                        ○ ← Not completed
Day 30: Export first report                            ○
Day 45: Configure integration                          ○
Day 60: Build custom dashboard                         ○

Adoption Score: 57% (4 of 7 milestones)
Status: On track but automation milestone overdue

Recommendation:
- Schedule enablement session for automation setup
- Automation adoption correlates with 2.3x higher retention
```

### Usage Benchmarking

| Metric | Your Average | Industry 25th | Industry 50th | Industry 75th |
|--------|--------------|---------------|---------------|---------------|
| DAU/MAU | 28% | 18% | 25% | 35% |
| Feature Adoption | 52% | 35% | 48% | 62% |
| Sessions/Week | 3.2 | 2.0 | 3.5 | 5.0 |
| Power User % | 22% | 12% | 20% | 30% |

### Alert Configuration

| Trigger | Threshold | Severity | Action |
|---------|-----------|----------|--------|
| No login | 14+ days | Warning | Automated re-engagement email |
| No login | 30+ days | High | CSM outreach |
| Usage decline | >25% MoM | High | CSM intervention |
| Usage decline | >50% MoM | Critical | Manager escalation |
| Key user inactive | 7+ days | High | Immediate outreach |
| Feature abandonment | Core feature unused 14+ days | Medium | Usage training |
| Seat utilization | <50% active | Medium | License optimization |

### Good Usage Analysis

```
Usage Deep Dive: Declining Account

Account: TechCorp Inc.
Health Score: 48 (was 72 three months ago)
Usage Trend: -34% over 90 days

Root Cause Analysis:

1. Champion Departure (Primary)
   - Sarah Chen (main user, 45% of all activity) left company
   - Remaining users haven't increased usage
   - No new champion identified

2. Feature Concentration Risk
   - 80% of usage was in 2 features
   - Those features are now unused
   - Other features never adopted

3. Team Turnover
   - 3 of 8 licensed users are new (last 60 days)
   - New users have not completed onboarding
   - No enablement sessions scheduled

Recommendations:
1. Schedule call with new stakeholder to identify champion
2. Arrange onboarding for 3 new users
3. Feature adoption push for underutilized capabilities
4. Consider usage-based pricing adjustment if team shrinks further
```

### Usage Metrics Collection Checklist

```
□ Activity Tracking
  □ Login events with timestamp
  □ Session duration
  □ User identification
  □ Device/platform tracking

□ Engagement Tracking
  □ Feature usage events
  □ Actions per session
  □ Time spent per feature
  □ Navigation patterns

□ Adoption Tracking
  □ Feature first-use detection
  □ Milestone completion
  □ Workflow completion rates
  □ Feature breadth score

□ Aggregations
  □ Daily/weekly/monthly rollups
  □ User-level aggregations
  □ Account-level rollups
  □ Trend calculations

□ Alerting
  □ Inactivity alerts
  □ Decline alerts
  □ Anomaly detection
  □ Threshold breach notifications

□ Visualization
  □ Real-time dashboards
  □ Historical trends
  □ Cohort comparisons
  □ Benchmark overlays
```

### Anti-Patterns

- **Vanity metrics** — Total logins don't predict retention
- **All-time totals** — Recent activity matters more
- **No user segmentation** — Average usage hides problems
- **Ignoring depth** — Login without action isn't engagement
- **Missing trends** — Snapshots without trajectories
- **No benchmarks** — Can't assess without comparison
- **Feature obsession** — Activity without value delivery
- **Data silos** — Usage disconnected from health scores
