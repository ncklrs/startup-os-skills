---
title: Success Metrics Definition
impact: HIGH
tags: metrics, kpis, measurement, analytics, success-criteria
---

## Success Metrics Definition

**Impact: HIGH**

Success metrics answer the most important question: "Did we build the right thing?" Without clear metrics, you're shipping features into a void and can't learn or iterate effectively.

### Why Define Metrics Upfront

1. **Alignment** — Everyone agrees what success looks like
2. **Prioritization** — Focus on what moves metrics
3. **Learning** — Understand what works and what doesn't
4. **Accountability** — Clear ownership of outcomes
5. **Resource allocation** — Data-driven investment decisions

### Metric Types

| Type | Purpose | Example | Timeframe |
|------|---------|---------|-----------|
| **Primary** | Core success measure | Conversion rate | Per feature |
| **Secondary** | Supporting indicators | Time to first action | Per feature |
| **Guardrail** | Ensure no regression | Page load time | Always |
| **Input** | Leading indicators | Signup attempts | Short-term |
| **Output** | Lagging results | Revenue | Long-term |

### The Metrics Hierarchy

```
                    ┌─────────────────────┐
                    │   North Star        │
                    │ (Company success)   │
                    └──────────┬──────────┘
                               │
            ┌──────────────────┼──────────────────┐
            │                  │                  │
     ┌──────┴──────┐    ┌──────┴──────┐    ┌──────┴──────┐
     │   Pillar 1  │    │   Pillar 2  │    │   Pillar 3  │
     │ Acquisition │    │  Activation │    │  Retention  │
     └──────┬──────┘    └──────┬──────┘    └──────┬──────┘
            │                  │                  │
     ┌──────┴──────┐    ┌──────┴──────┐    ┌──────┴──────┐
     │  Feature    │    │  Feature    │    │  Feature    │
     │  Metrics    │    │  Metrics    │    │  Metrics    │
     └─────────────┘    └─────────────┘    └─────────────┘
```

### SMART Metrics Framework

Every metric should be:

| Criteria | Question | Bad Example | Good Example |
|----------|----------|-------------|--------------|
| **S**pecific | What exactly are we measuring? | "Engagement" | "DAU/MAU ratio" |
| **M**easurable | Can we actually track it? | "User happiness" | "NPS score" |
| **A**chievable | Is the target realistic? | "100% retention" | "85% 30-day retention" |
| **R**elevant | Does it matter for this feature? | "Total users" (for niche feature) | "Feature adoption rate" |
| **T**ime-bound | When do we measure? | "Eventually improve" | "Increase 10% by Q2" |

### Metrics Definition Template

```markdown
## Metric: [Name]

### Definition
| Property | Value |
|----------|-------|
| Name | Active Team Workspaces |
| Definition | Workspaces with ≥2 members and activity in last 7 days |
| Formula | COUNT(workspaces WHERE member_count >= 2 AND last_activity > now() - 7d) |
| Type | Primary |
| Owner | Product Team |

### Context
**Why this metric matters:**
Measures whether teams are getting value from the sharing feature.
Directly tied to team plan retention.

**How it connects to business goals:**
North Star: Weekly Active Teams
Pillar: Team Activation
This metric: Feature-level success

### Measurement

**Data Source:** Analytics warehouse (Snowflake)
**Calculation Frequency:** Daily
**Dashboard:** [Link to dashboard]
**Alert Threshold:** <90% of target for 3 consecutive days

### Targets

| Period | Baseline | Target | Stretch |
|--------|----------|--------|---------|
| Launch (Week 1) | 0 | 100 | 200 |
| Month 1 | 100 | 500 | 750 |
| Month 3 | 500 | 2,000 | 3,000 |
| Month 6 | 2,000 | 5,000 | 7,500 |

### Segments

Track this metric by:
- Plan type (Free, Teams, Enterprise)
- Company size (1-10, 11-50, 51-200, 200+)
- Acquisition cohort (month signed up)
- Geography (US, EU, APAC, Other)

### Caveats
- Excludes test/demo accounts
- "Activity" = any create/edit/view event
- Gaming risk: Low (activity definition is broad)
```

### Good Metrics Specification Example

```markdown
# Success Metrics: Workspace Sharing Feature

## Overview

| Metric Type | Metric | Target | Measurement |
|-------------|--------|--------|-------------|
| Primary | Team activation rate | 30% | % of Teams accounts using sharing |
| Secondary | Time to first invite | <24 hours | Median time from workspace creation |
| Guardrail | Workspace load time | <2s p95 | No regression from adding sharing |
| Input | Invitations sent | 1,000/week | Leading indicator of adoption |

## Primary Metric: Team Activation Rate

### Definition
Percentage of Teams plan accounts that have invited at least one
member to at least one workspace within 30 days of signing up.

### Formula
```
team_activation_rate =
  COUNT(teams_accounts WHERE invited_member = true AND account_age <= 30d)
  / COUNT(teams_accounts WHERE account_age <= 30d)
```

### Why This Metric
- Directly measures if teams are getting value
- Predictive of retention (correlated 0.7)
- Actionable (we can improve invitation flow)
- Not gameable (requires real action)

### Current State
- Baseline: N/A (new feature)
- Comparable: Email invitation rate = 15%
- Industry benchmark: Team features ~25-35%

### Targets

| Milestone | Target | Rationale |
|-----------|--------|-----------|
| Week 1 | 5% | Early adopters only |
| Month 1 | 15% | Ramp with awareness |
| Month 3 | 25% | Optimization based on learning |
| Month 6 | 35% | Mature adoption |

### Segmentation
- By plan tier (Teams vs Enterprise)
- By company size
- By acquisition channel
- By industry vertical

## Secondary Metric: Time to First Invite

### Definition
Median time from workspace creation to first invitation sent,
for workspaces that eventually have invitations.

### Formula
```
time_to_first_invite = MEDIAN(
  first_invitation_timestamp - workspace_created_timestamp
  WHERE workspace.invitation_count > 0
)
```

### Why This Metric
- Measures friction in invitation flow
- Faster = better user experience
- Can optimize specific steps

### Current State
- Baseline: N/A (new feature)
- Hypothesis: <24 hours is healthy

### Targets

| Milestone | Target | Rationale |
|-----------|--------|-----------|
| Launch | <48 hours | Initial discovery |
| Month 1 | <24 hours | Improved onboarding |
| Month 3 | <12 hours | Streamlined flow |

## Guardrail Metric: Workspace Load Time

### Definition
95th percentile page load time for workspace pages.

### Why This Metric
Ensure sharing feature doesn't regress core experience.

### Threshold
- Current baseline: 1.8s p95
- Maximum acceptable: 2.0s p95
- Alert if: >2.0s for 15 minutes

### Action if Breached
1. Roll back sharing feature
2. Investigate performance
3. Optimize before re-enabling

## Input Metric: Invitations Sent

### Definition
Total number of workspace invitations sent per week.

### Why This Metric
Leading indicator of adoption. If invitations drop, investigate
before it affects activation rate.

### Targets

| Week | Target | Notes |
|------|--------|-------|
| 1 | 100 | Internal + alpha |
| 2 | 300 | Beta expansion |
| 3 | 700 | Wider beta |
| 4 | 1,500 | GA |
| Steady state | 2,000+/week | Ongoing |

## Metric Dependencies

```
Invitations Sent (Input)
        │
        ▼
Invitations Accepted (Conversion)
        │
        ▼
Active Team Workspaces (Engagement)
        │
        ▼
Team Activation Rate (Primary)
        │
        ▼
Team Plan Retention (Business Outcome)
```

## Dashboard Requirements

### Real-time View
- Invitations sent (last 24 hours)
- Error rates
- Load times

### Daily View
- Activation rate trend
- Time to first invite distribution
- Funnel conversion rates

### Weekly View
- Segment breakdown
- Cohort analysis
- Feature usage patterns

## Analytics Events

| Event | Trigger | Properties |
|-------|---------|------------|
| `invitation_sent` | Invite submitted | workspace_id, permission_level |
| `invitation_accepted` | Invite clicked and accepted | workspace_id, days_pending |
| `invitation_expired` | 7-day expiration | workspace_id |
| `member_added` | User joins workspace | workspace_id, source |
| `member_removed` | User removed/leaves | workspace_id, reason |
```

### Bad Metrics Specification Example

```markdown
# Metrics: Sharing Feature

We will track:
- Number of users
- Engagement
- Customer satisfaction

Success = people use it.
```

**Why it fails:**
- No specific definitions
- No targets or baselines
- "Engagement" and "satisfaction" undefined
- No timeframes
- No measurement plan

### Common Metrics by Feature Type

| Feature Type | Primary Metric | Secondary Metrics |
|--------------|----------------|-------------------|
| **Onboarding** | Activation rate | Time to first value, drop-off points |
| **Engagement** | DAU/MAU ratio | Session length, feature usage |
| **Conversion** | Conversion rate | Funnel step rates, time to convert |
| **Retention** | D7/D30 retention | Churn rate, resurrection rate |
| **Revenue** | ARPU, LTV | Upgrade rate, expansion revenue |
| **Performance** | Page load time | Error rate, availability |
| **Support** | Ticket volume | Resolution time, CSAT |

### Metrics Pitfalls to Avoid

| Pitfall | Problem | Solution |
|---------|---------|----------|
| **Vanity metrics** | Big numbers that don't matter | Focus on actionable metrics |
| **Gaming** | Metric improves without real progress | Use multiple metrics, monitor behavior |
| **Short-termism** | Optimize metric, hurt long-term | Add guardrail metrics |
| **Over-measurement** | Track everything, act on nothing | Limit to 3-5 key metrics |
| **Stale targets** | Targets don't evolve with learning | Review quarterly |

### Metrics Review Cadence

| Frequency | Review | Participants |
|-----------|--------|--------------|
| Daily | Real-time dashboards | Engineering |
| Weekly | Metric trends, anomalies | Product + Engineering |
| Monthly | Progress to targets | Leadership |
| Quarterly | Target recalibration | Exec team |

### Anti-Patterns

- **Metric theater** — Tracking metrics without acting on them
- **Goal post moving** — Changing targets when you miss them
- **Survivor bias** — Only measuring users who stuck around
- **Correlation confusion** — Assuming causation from correlation
- **Local optimization** — Improving metric while hurting overall experience
- **Metric debt** — Accumulating measurements nobody uses
- **Undefined baseline** — Targets without knowing where you're starting
- **Success by omission** — Not measuring what might show failure
- **Proxy obsession** — Optimizing proxy instead of real outcome
- **Launch and forget** — Setting metrics at launch, never reviewing
