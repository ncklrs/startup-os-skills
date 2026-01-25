---
title: SLA Design & Compliance
impact: CRITICAL
tags: sla, service-level, compliance, response-time, resolution
---

## SLA Design & Compliance

**Impact: CRITICAL**

Service Level Agreements define customer expectations and team accountability. Well-designed SLAs balance customer needs with operational capacity. Poorly designed SLAs create false promises, stressed agents, and dissatisfied customers.

### SLA Components

| Component | Definition | Example |
|-----------|------------|---------|
| **First Response Time** | Time to initial acknowledgment | "We'll respond within 1 hour" |
| **Resolution Time** | Time to issue closure | "We'll resolve within 24 hours" |
| **Update Frequency** | Time between status updates | "Updates every 4 hours until resolved" |
| **Business Hours** | When SLA clock runs | "9am-6pm PST, Mon-Fri" |
| **Escalation Trigger** | When to escalate automatically | "If unresolved after 80% of SLA" |

### SLA by Priority Level

| Priority | First Response | Resolution | Update Frequency |
|----------|---------------|------------|------------------|
| **P1 Critical** | 15 minutes | 4 hours | Every 30 minutes |
| **P2 High** | 1 hour | 8 hours | Every 2 hours |
| **P3 Medium** | 4 hours | 24 hours | Every 8 hours |
| **P4 Low** | 8 hours | 72 hours | Every 24 hours |
| **P5 Request** | 24 hours | 5 business days | At status change |

### SLA by Customer Tier

| Tier | Multiplier | P1 Response | P1 Resolution |
|------|------------|-------------|---------------|
| **Enterprise** | 0.5x (faster) | 7 minutes | 2 hours |
| **Business** | 1x (standard) | 15 minutes | 4 hours |
| **Professional** | 1.5x | 30 minutes | 6 hours |
| **Starter** | 2x | 1 hour | 8 hours |
| **Free** | 4x | 4 hours | Next business day |

### Good SLA Design

```
✓ Realistic targets
  → Based on historical data and capacity
  → Buffer for complexity variation
  → Achievable 95% of the time

✓ Clear definitions
  → What counts as "response"?
  → What counts as "resolution"?
  → When does clock start/stop?

✓ Business hours clarity
  → Defined time zones
  → Holiday calendars
  → 24/7 for critical only

✓ Escalation automation
  → Warning at 80% of SLA
  → Auto-escalate at breach
  → Visibility to managers

✓ Regular review
  → Monthly SLA performance analysis
  → Adjust based on capacity
  → Customer feedback incorporation
```

### Bad SLA Design

```
✗ Promise more than you can deliver
  → 15-minute response with 2 agents
  → Creates breach patterns

✗ Same SLA for all priorities
  → P4 tickets block P1 attention
  → Resources misallocated

✗ Vague definitions
  → "We'll get back to you soon"
  → No measurable commitment

✗ 24/7 claims without 24/7 staff
  → SLA breaches overnight/weekends
  → Angry customers Monday morning

✗ No pause mechanism
  → Clock runs while waiting on customer
  → Unfair agent metrics

✗ SLA as punishment
  → Metrics used to penalize, not improve
  → Gaming behavior emerges
```

### SLA Clock Rules

| Event | Clock Behavior |
|-------|----------------|
| Ticket created | Clock starts |
| Agent responds | Response SLA met |
| Status → Pending Customer | Clock pauses |
| Customer responds | Clock resumes |
| Status → Resolved | Resolution SLA met |
| Ticket reopened | New SLA period begins |
| Business hours end | Clock pauses (if applicable) |

### SLA Breach Prevention

| Warning Level | Trigger | Action |
|--------------|---------|--------|
| **Yellow** | 50% of SLA elapsed | Visible in queue view |
| **Orange** | 80% of SLA elapsed | Alert to assignee |
| **Red** | 90% of SLA elapsed | Alert to team lead |
| **Breach** | 100% elapsed | Manager notification, escalation |
| **Severe Breach** | 2x SLA elapsed | Director notification |

### SLA Compliance Dashboard

| Metric | Calculation | Target |
|--------|-------------|--------|
| **Response SLA %** | Met / Total tickets | 95%+ |
| **Resolution SLA %** | Met / Total tickets | 90%+ |
| **Avg Time to First Response** | Sum(response times) / count | <50% of SLA |
| **Avg Resolution Time** | Sum(resolution times) / count | <75% of SLA |
| **Breach Count** | Tickets past SLA | Trending down |
| **Severe Breach Count** | Tickets 2x+ past SLA | Zero |

### SLA Reporting Cadence

| Report | Frequency | Audience |
|--------|-----------|----------|
| **Real-time dashboard** | Live | Agents, leads |
| **Daily summary** | Daily | Managers |
| **Weekly analysis** | Weekly | Directors |
| **Monthly review** | Monthly | VP, execs |
| **Quarterly trends** | Quarterly | C-level, board |

### SLA Exception Handling

| Exception | How to Handle |
|-----------|---------------|
| **Customer unresponsive** | Pause clock after 2 follow-ups |
| **Third-party dependency** | Document, may pause clock |
| **Product bug requires fix** | Track separately, link to bug |
| **Out of scope request** | Close with explanation, no breach |
| **Duplicate ticket** | Merge, use original SLA |
| **Customer requests pause** | Pause with documentation |

### SLA Template

```
## [Company Name] Support SLA

### Coverage Hours
Support is available Monday-Friday, 9:00 AM - 6:00 PM [Timezone].
Critical (P1) issues receive 24/7 coverage.

### Response Time Commitments

| Priority | Description | First Response | Resolution Target |
|----------|-------------|----------------|-------------------|
| Critical | System outage | 15 minutes | 4 hours |
| High | Major feature broken | 1 hour | 8 hours |
| Medium | Feature impaired | 4 hours | 24 hours |
| Low | Minor issue | 8 hours | 72 hours |

### Definitions
- **First Response**: Initial acknowledgment from support agent
- **Resolution**: Issue resolved or workaround provided
- **Business Hours**: Clock pauses outside coverage hours (except P1)

### Escalation
Tickets approaching SLA are automatically escalated to team leads.
SLA breaches are reported to management for review.

### Exclusions
SLA does not apply to: feature requests, out-of-scope issues,
or delays caused by customer unresponsiveness.
```

### SLA Implementation Checklist

```
Design Phase:
□ Analyze historical ticket data
□ Calculate current response/resolution times
□ Set targets based on capacity + 20% buffer
□ Define clear priority criteria
□ Document business hours and holidays
□ Create customer tier matrix

Configuration Phase:
□ Set up SLA policies in help desk
□ Configure clock pause rules
□ Create escalation workflows
□ Build breach notifications
□ Set up reporting dashboards

Launch Phase:
□ Train agents on SLA expectations
□ Communicate SLA to customers
□ Monitor closely for first 2 weeks
□ Adjust unrealistic targets
□ Celebrate compliance wins
```

### Anti-Patterns

- **Vanity SLAs** — Impressive numbers no one can meet
- **Clock manipulation** — Pausing for illegitimate reasons
- **Resolution without resolution** — Closing tickets to hit SLA
- **One SLA fits all** — Same targets for all ticket types
- **SLA without capacity** — Promises without staffing to deliver
- **Breach normalization** — Accepting regular breaches as normal
- **Customer tier opacity** — Customers don't know their SLA level
