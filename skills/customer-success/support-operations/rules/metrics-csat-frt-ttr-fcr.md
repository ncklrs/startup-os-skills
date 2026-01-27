---
title: Support Metrics (CSAT, FRT, TTR, FCR)
impact: HIGH
tags: metrics, CSAT, FRT, TTR, FCR, NPS, analytics, performance
---

## Support Metrics (CSAT, FRT, TTR, FCR)

**Impact: HIGH**

What gets measured gets managed. The right metrics drive the right behaviors. Wrong metrics create perverse incentives. Support metrics should measure customer outcomes, not just agent activity.

### Core Metrics Overview

| Metric | Full Name | What It Measures | Target |
|--------|-----------|------------------|--------|
| **CSAT** | Customer Satisfaction | Customer happiness | 90%+ |
| **FRT** | First Response Time | Speed to acknowledge | <1 hour |
| **TTR** | Time to Resolution | Speed to solve | <24 hours |
| **FCR** | First Contact Resolution | Solved without escalation | 70%+ |
| **NPS** | Net Promoter Score | Loyalty/advocacy | 30+ |
| **CES** | Customer Effort Score | Ease of resolution | <2 (low effort) |

### Metric Formulas

```
CSAT = (Satisfied Responses / Total Responses) × 100
Target: 90%+ | Warning: <85%

FRT = Sum(First Response Times) / Total Tickets
Target: <1 hour | Warning: >4 hours

TTR = Sum(Resolution Times) / Total Resolved Tickets
Target: <24 hours | Warning: >72 hours

FCR = (Tickets Resolved on First Contact / Total Tickets) × 100
Target: 70%+ | Warning: <50%

NPS = % Promoters (9-10) - % Detractors (0-6)
Target: 30+ | Warning: <10

Reopen Rate = (Reopened Tickets / Resolved Tickets) × 100
Target: <5% | Warning: >10%
```

### The Metrics Hierarchy

```
┌─────────────────────────────────────────────────────────────────┐
│                     BUSINESS OUTCOMES                            │
│  Customer retention, expansion, advocacy, cost efficiency        │
├─────────────────────────────────────────────────────────────────┤
│                     CUSTOMER EXPERIENCE                          │
│  CSAT, NPS, CES, Customer Lifetime Value                         │
├─────────────────────────────────────────────────────────────────┤
│                     OPERATIONAL METRICS                          │
│  FRT, TTR, FCR, SLA compliance, backlog, escalation rate        │
├─────────────────────────────────────────────────────────────────┤
│                     ACTIVITY METRICS                             │
│  Tickets handled, handle time, utilization, replies per ticket  │
└─────────────────────────────────────────────────────────────────┘
```

### Good Metric Practices

```
✓ Measure outcomes, not just activity
  → CSAT over tickets closed
  → FCR over speed alone
  → Quality over quantity

✓ Context with metrics
  → Segment by ticket type
  → Compare similar complexity
  → Account for team differences

✓ Balanced scorecard
  → Speed + Quality + Volume
  → No single metric obsession
  → Trade-offs acknowledged

✓ Agent-level + Team-level
  → Individual accountability
  → Team collaboration visible
  → Neither in isolation

✓ Regular calibration
  → Define what "good" looks like
  → Review outliers
  → Adjust targets based on data
```

### Bad Metric Practices

```
✗ Vanity metrics
  → "We closed 1000 tickets!"
  → (But 400 were reopened)

✗ Speed at all costs
  → Racing to respond/close
  → Quality sacrificed

✗ Gaming the system
  → Closing to hit targets
  → Solving easy tickets only
  → Marking pending to pause clock

✗ Metrics without context
  → Comparing unlike tickets
  → Ignoring complexity factors

✗ Punishment-focused
  → Metrics used to punish
  → Fear-based culture
  → Hide problems instead of solve

✗ Single metric obsession
  → Optimize FRT, ignore quality
  → Hit FCR, don't escalate (badly)
```

### CSAT Deep Dive

| Score | Meaning | Action |
|-------|---------|--------|
| 5 | Very Satisfied | Identify what worked, replicate |
| 4 | Satisfied | Good, look for improvement areas |
| 3 | Neutral | Investigate, follow up |
| 2 | Dissatisfied | Immediate follow-up required |
| 1 | Very Dissatisfied | Manager review, service recovery |

**CSAT Survey Best Practices:**
```
✓ Send within 24 hours of resolution
✓ Keep survey short (1-3 questions)
✓ Include open-ended comment field
✓ Follow up on low scores within 24 hours
✓ Track CSAT by agent, category, complexity

Sample Survey:
1. How satisfied are you with your support experience? (1-5)
2. [Optional] What could we have done better?
3. [Optional] Anything else you'd like to share?
```

### Agent Performance Dashboard

| Metric | What It Shows | Review Frequency |
|--------|---------------|------------------|
| **CSAT (individual)** | Agent quality | Weekly |
| **Tickets handled** | Productivity | Daily |
| **Avg handle time** | Efficiency | Weekly |
| **FCR rate** | Resolution skill | Weekly |
| **Escalation rate** | Self-sufficiency | Weekly |
| **Reopen rate** | Resolution quality | Weekly |
| **QA score** | Process adherence | Weekly |
| **Utilization** | Time on tickets | Daily |

### Team Performance Dashboard

| Metric | What It Shows | Review Frequency |
|--------|---------------|------------------|
| **CSAT (team)** | Overall quality | Daily |
| **SLA compliance** | Promise keeping | Real-time |
| **Backlog** | Capacity health | Real-time |
| **Wait time** | Customer experience | Real-time |
| **Escalation volume** | L2/L3 load | Daily |
| **Trending issues** | Product problems | Daily |
| **Channel mix** | Resource allocation | Weekly |

### Quality Assurance Scoring

| Dimension | Weight | Criteria |
|-----------|--------|----------|
| **Solution Quality** | 30% | Correct, complete, first-time |
| **Communication** | 25% | Clear, empathetic, professional |
| **Process Adherence** | 20% | Followed procedures, documentation |
| **Efficiency** | 15% | Appropriate handle time, no waste |
| **Customer Experience** | 10% | Tone, personalization, going extra mile |

**Sample QA Rubric:**
```
□ Greeting was professional and personalized
□ Issue was correctly understood and restated
□ Troubleshooting was logical and complete
□ Solution was correct and clearly explained
□ Next steps were provided
□ Ticket was properly categorized and documented
□ Tone was empathetic and appropriate
□ Handle time was reasonable for complexity
```

### Reporting Cadence

| Report | Metrics Included | Audience | Frequency |
|--------|------------------|----------|-----------|
| **Agent Dashboard** | Personal stats | Agents | Real-time |
| **Team Standup** | Daily snapshot | Team leads | Daily |
| **Weekly Review** | Trends, outliers | Managers | Weekly |
| **Monthly Business Review** | Strategic metrics | Directors | Monthly |
| **Quarterly Board Report** | Cost, CSAT, NPS | Executives | Quarterly |

### Benchmarks by Company Stage

| Stage | CSAT | FRT | TTR | FCR |
|-------|------|-----|-----|-----|
| **Startup** | 85%+ | <4 hours | <48 hours | 60%+ |
| **Growth** | 88%+ | <2 hours | <24 hours | 65%+ |
| **Scale** | 90%+ | <1 hour | <12 hours | 70%+ |
| **Enterprise** | 92%+ | <30 min | <8 hours | 75%+ |

### Diagnosing Metric Problems

| Symptom | Possible Causes | Investigation |
|---------|-----------------|---------------|
| Low CSAT | Wrong solutions, bad communication | QA reviews, comment analysis |
| High FRT | Understaffed, poor routing | Capacity analysis, queue review |
| Low FCR | Knowledge gaps, over-escalation | Training needs, KB gaps |
| High reopens | Premature closure, wrong solutions | QA reviews, root cause analysis |
| High escalation | L1 undertrained, complexity increase | Skill assessment, ticket analysis |

### Metric Improvement Playbook

```
CSAT Improvement:
1. Analyze low-score tickets for patterns
2. Implement service recovery for 1-2 scores
3. Train on communication and empathy
4. Add quality checkpoints before closure
5. Recognize and share high-CSAT behaviors

FCR Improvement:
1. Identify common escalation reasons
2. Create KB articles for top escalations
3. Train L1 on frequently escalated topics
4. Empower L1 with more resolution authority
5. Add decision trees for complex issues
```

### Anti-Patterns

- **CSAT gaming** — Only surveying easy tickets
- **FRT racing** — Copy-paste first response to hit metric
- **Premature closure** — Closing to hit TTR, causing reopens
- **FCR inflation** — Not escalating when you should
- **Metric of the month** — Constantly changing focus
- **Comparison without context** — Ignoring ticket complexity
- **Activity over outcomes** — Celebrating tickets closed, not problems solved
- **Individual over team** — Missing collaborative behaviors
