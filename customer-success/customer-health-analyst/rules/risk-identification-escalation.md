---
title: Risk Identification & Escalation
impact: CRITICAL
tags: risk-identification, escalation, intervention, save-strategies
---

## Risk Identification & Escalation

**Impact: CRITICAL**

Early risk identification and well-defined escalation processes are the difference between saving an at-risk account and conducting a post-mortem. A structured approach ensures no customer falls through the cracks and interventions happen with enough lead time to succeed.

### The Risk Escalation Framework

```
┌──────────────────────────────────────────────────────────────────┐
│                     RISK ESCALATION PATH                         │
├──────────────────────────────────────────────────────────────────┤
│                                                                  │
│  LOW RISK          MEDIUM RISK        HIGH RISK        CRITICAL │
│  Health: 70+       Health: 50-69      Health: 30-49    Health: <30│
│                                                                  │
│  ┌─────────┐      ┌─────────┐       ┌─────────┐      ┌─────────┐│
│  │ Monitor │ ───► │ Engage  │ ────► │Intervene│ ───► │Escalate ││
│  └─────────┘      └─────────┘       └─────────┘      └─────────┘│
│                                                                  │
│  Owner: CSM       Owner: CSM        Owner: CSM +     Owner: VP + │
│                                     Manager          Executive   │
│                                                                  │
│  SLA: Weekly      SLA: 1 week       SLA: 48 hours   SLA: 24 hrs │
│  review           outreach          intervention    response     │
│                                                                  │
└──────────────────────────────────────────────────────────────────┘
```

### Risk Signal Categories

| Category | Signals | Severity | Detection Method |
|----------|---------|----------|------------------|
| **Usage** | Declining logins, feature abandonment, dormant users | High | Product analytics |
| **Engagement** | Missed meetings, unresponsive, no exec access | High | CRM tracking |
| **Sentiment** | Negative NPS, complaints, support escalations | High | Survey + Support |
| **Financial** | Payment issues, contract questions, budget concerns | Very High | Billing + CSM notes |
| **Organizational** | Champion leaving, reorg, M&A | Critical | LinkedIn + news |
| **Competitive** | Competitor mentions, RFP activity, feature comparisons | Very High | Call transcripts |
| **Contractual** | Short contract, no auto-renew, upcoming expiration | Medium | Contract data |

### Risk Signal Severity Matrix

| Signal | Severity | Time Sensitivity | Required Action |
|--------|----------|------------------|-----------------|
| Champion departure | Critical | 24 hours | Executive outreach |
| Cancellation request | Critical | Same day | Save team activation |
| Competitor evaluation | Very High | 48 hours | Executive involvement |
| Usage decline >50% | High | 48 hours | CSM intervention |
| Payment failure | High | 24 hours | Billing + CSM outreach |
| Negative NPS response | High | 72 hours | Closed-loop follow-up |
| Missed QBR | Medium | 1 week | Manager involvement |
| Contract expiring <90 days | Medium | 1 week | Renewal discussion |
| Support escalation | Medium | 48 hours | Service recovery |

### Good Risk Identification System

```
Risk Alert: Acme Corp

Account: Acme Corp
ARR: $125,000
Health Score: 42 (was 68 last month)
CSM: Jane Smith

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

RISK SIGNALS DETECTED:

1. Champion Status Change (CRITICAL)
   └── Sarah Johnson updated LinkedIn to new company
   └── Detected: 2 hours ago
   └── She represented 65% of account activity

2. Usage Decline (HIGH)
   └── 34% decrease in DAU over 30 days
   └── Key feature "Reports" unused for 14 days
   └── Trend accelerating

3. Support Sentiment (MEDIUM)
   └── Last 3 tickets rated "Dissatisfied"
   └── Average sentiment score: 2.1/5 (was 4.2)

RISK SCORE: 78/100 (High Risk)

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

RECOMMENDED ACTIONS:

1. [IMMEDIATE] Contact account to identify new champion
2. [48 HOURS] Schedule executive check-in
3. [1 WEEK] Arrange re-onboarding for new stakeholders

ESCALATION: Manager + VP CS notified
SLA: Response required within 24 hours
```

### Bad Risk Identification System

```
Alert: Account health decreased

Account: Acme Corp
Health Score: 42
Alert: Health score below threshold

Problems:
✗ No specific signals identified
✗ No context on what changed
✗ No severity classification
✗ No recommended actions
✗ No escalation path
✗ No SLA defined
✗ No ARR/impact context
```

### Escalation Matrix

| Trigger | First Responder | Escalate To | Executive Involvement |
|---------|-----------------|-------------|----------------------|
| Health drops >15 points | CSM | None initially | If no improvement in 2 weeks |
| Health drops >25 points | CSM | CSM Manager | VP if no improvement in 1 week |
| Health score <40 | CSM + Manager | VP CS | CEO for strategic accounts |
| Churn signal detected | CSM | Manager + VP | Based on ARR tier |
| Champion departure | CSM | Manager | VP for accounts >$100K |
| Competitive threat | CSM + Manager | VP CS + Exec | CEO for strategic |
| Cancellation request | Save Team | VP CS | CEO for top 20 accounts |

### Intervention Playbooks

**Playbook: Champion Departure**

```
Trigger: Key contact leaves company
Severity: Critical
SLA: 24 hour initial response

Day 1:
□ Verify departure (LinkedIn, email bounce, etc.)
□ Identify replacement contact
□ Executive-to-executive outreach to maintain relationship
□ Update CRM with new stakeholder map

Day 2-7:
□ Schedule intro call with new champion
□ Offer re-onboarding/training
□ QBR to re-establish value baseline
□ Document new success criteria

Day 8-30:
□ Accelerate engagement cadence
□ Monthly check-ins (vs. quarterly)
□ Feature adoption review
□ Executive sponsor assignment if needed
```

**Playbook: Usage Decline**

```
Trigger: Usage down >25% over 30 days
Severity: High
SLA: 48 hour initial contact

Day 1-2:
□ Analyze usage data for root cause
□ Identify which users/features affected
□ CSM outreach: "I noticed [specific change], is everything okay?"
□ Offer support call

Day 3-7:
□ Deep-dive call to understand context
□ Create action plan with customer
□ Enablement session if adoption issue
□ Executive involvement if strategic issue

Day 8-30:
□ Weekly check-ins during recovery
□ Monitor usage daily
□ Adjust plan based on progress
□ Escalate if no improvement by day 14
```

**Playbook: Competitive Threat**

```
Trigger: Competitor mention detected
Severity: Very High
SLA: 48 hour executive response

Day 1:
□ Alert CSM, Manager, and VP
□ Gather intelligence (what competitor, why looking)
□ Prepare competitive battle card
□ Schedule executive call

Day 2-3:
□ Executive-to-executive engagement
□ Understand specific evaluation criteria
□ Address gaps or concerns directly
□ Reinforce unique value proposition

Day 4-14:
□ Provide additional proof points (case studies, ROI)
□ Offer executive references
□ Consider strategic concessions if needed
□ Document outcome and learnings
```

### Save Team Structure

| Role | Responsibility | When Engaged |
|------|----------------|--------------|
| **CSM** | First line, relationship management | Always |
| **CSM Manager** | Strategy, additional resources | Health <50 |
| **VP Customer Success** | Executive relationships, approvals | Health <35 or $100K+ ARR |
| **Executive Sponsor** | Peer-level engagement | Strategic accounts |
| **Product** | Roadmap discussions, custom solutions | Feature gaps |
| **Finance** | Pricing, contract flexibility | Commercial objections |

### Save Offer Guidelines

| Offer Type | When to Use | Approval Required | Success Rate |
|------------|-------------|-------------------|--------------|
| Extended support | Adoption/enablement issues | CSM | 45% |
| Professional services | Implementation gaps | Manager | 40% |
| Feature access | Missing functionality | Manager | 35% |
| Contract pause | Timing/budget issues | VP | 30% |
| Pricing concession | Cost objections | VP + Finance | 25% |
| Custom development | Critical feature gap | Executive | 20% |

### Risk Review Cadence

| Review Type | Frequency | Attendees | Focus |
|-------------|-----------|-----------|-------|
| **Daily Standup** | Daily | CSM Team | Critical alerts |
| **Team Review** | Weekly | CSM + Manager | At-risk accounts |
| **Leadership Review** | Weekly | VP + Directors | High-value at-risk |
| **Executive Review** | Monthly | C-Suite | Strategic accounts |
| **Portfolio Review** | Quarterly | All CS | Trends, patterns |

### Risk Documentation Template

```
## At-Risk Account Analysis

**Account:** [Name]
**ARR:** [Amount]
**Health Score:** [Current] (was [Previous])
**Risk Level:** [Critical/High/Medium]
**Date Identified:** [Date]

### Risk Signals
| Signal | Severity | Date Detected |
|--------|----------|---------------|
| [Signal 1] | [Level] | [Date] |
| [Signal 2] | [Level] | [Date] |

### Root Cause Analysis
[What's driving the risk]

### Stakeholder Impact
- Champion: [Status]
- Executive Sponsor: [Status]
- End Users: [Status]

### Action Plan
| Action | Owner | Due Date | Status |
|--------|-------|----------|--------|
| [Action 1] | [Name] | [Date] | [Status] |
| [Action 2] | [Name] | [Date] | [Status] |

### Outcome
[ ] Saved
[ ] Churned
[ ] In Progress

### Lessons Learned
[What we'll do differently]
```

### Escalation Checklist

```
□ Risk Identification
  □ Specific signals documented
  □ Severity classified correctly
  □ Root cause hypothesized
  □ ARR impact quantified

□ Initial Response
  □ CSM contacted within SLA
  □ Customer context gathered
  □ Quick win opportunities identified
  □ Escalation need assessed

□ Escalation Execution
  □ Right people involved
  □ Clear ask defined
  □ Timeline established
  □ Customer expectations set

□ Intervention
  □ Action plan created
  □ Customer agreement obtained
  □ Progress tracking in place
  □ Success criteria defined

□ Resolution
  □ Outcome documented
  □ Lessons captured
  □ Process improvements identified
  □ Stakeholders informed
```

### Anti-Patterns

- **Alert fatigue** — Too many low-priority alerts mask real risks
- **Single signal reliance** — Missing multi-factor risk patterns
- **Slow escalation** — Waiting too long to involve leadership
- **No playbooks** — Ad-hoc response to predictable situations
- **Discount-first saves** — Training customers to threaten churn
- **Ignoring small accounts** — Risk exists at all ARR levels
- **No documentation** — Same mistakes repeated
- **Hero culture** — Depending on individuals vs. process
