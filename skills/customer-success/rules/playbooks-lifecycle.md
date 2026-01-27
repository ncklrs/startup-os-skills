---
title: CS Playbook Development
impact: HIGH
tags: playbooks, lifecycle, automation, qbr, renewal, escalation
---

## CS Playbook Development

**Impact: HIGH**

Playbooks are the operating system of your CS organization. Without them, every CSM reinvents the wheel. With them, you scale best practices across the team and ensure consistent customer experiences.

### Playbook Categories

```
LIFECYCLE PLAYBOOKS (Proactive)
├── Onboarding Playbook
├── Adoption Playbook
├── Expansion Playbook
├── Renewal Playbook
└── Advocacy Playbook

INTERVENTION PLAYBOOKS (Reactive)
├── At-Risk Playbook
├── Escalation Playbook
├── Champion Change Playbook
└── Executive Sponsor Loss Playbook

OPERATIONAL PLAYBOOKS (Recurring)
├── QBR Playbook
├── EBR Playbook
├── Success Plan Playbook
└── Handoff Playbook
```

### Playbook Anatomy

```
┌─────────────────────────────────────────────────────────────────┐
│                       PLAYBOOK TEMPLATE                          │
├─────────────────────────────────────────────────────────────────┤
│ TRIGGER: What initiates this playbook?                          │
│ OWNER: Who is responsible?                                       │
│ TIMELINE: How long does this take?                              │
│ EXIT CRITERIA: How do we know it's complete?                    │
├─────────────────────────────────────────────────────────────────┤
│ STEPS:                                                           │
│ 1. Step name (Day X) - Channel - Owner                          │
│    • Action details                                             │
│    • Templates/resources                                        │
│    • Success criteria                                           │
│ 2. Step name (Day Y) - Channel - Owner                          │
│    ...                                                          │
├─────────────────────────────────────────────────────────────────┤
│ METRICS: How do we measure success?                             │
│ AUTOMATION: What can be automated?                              │
│ ESCALATION: When/how to escalate?                               │
└─────────────────────────────────────────────────────────────────┘
```

### Onboarding Playbook (High Touch)

| Day | Action | Owner | Channel | Goal |
|-----|--------|-------|---------|------|
| 0 | Welcome email with next steps | CSM | Email | Set expectations |
| 1 | Internal kickoff (sales handoff) | CSM + AE | Internal | Full context |
| 3 | External kickoff call | CSM | Video | Align on goals |
| 5 | Success plan draft sent | CSM | Email | Define outcomes |
| 7 | Success plan review call | CSM | Video | Finalize goals |
| 10 | Technical setup check | CSM | Email/Call | Remove blockers |
| 14 | First value checkpoint | CSM | Video | Confirm progress |
| 21 | Adoption review | CSM | Video | Feature adoption |
| 30 | Onboarding complete review | CSM | Video | Handoff to BAU |

**Exit Criteria:**
- [ ] Success plan documented and agreed
- [ ] Key stakeholders identified
- [ ] First value milestone achieved
- [ ] Product adoption >60%
- [ ] Health score >70

### Onboarding Playbook (Tech Touch)

| Day | Action | Channel | Trigger |
|-----|--------|---------|---------|
| 0 | Welcome email sequence starts | Email | Sign-up |
| 0 | In-app onboarding checklist | In-app | First login |
| 3 | Feature spotlight email | Email | Auto (Day 3) |
| 5 | Usage tips based on behavior | In-app | Feature usage |
| 7 | Check-in email (need help?) | Email | Auto (Day 7) |
| 14 | Adoption milestone email | Email | Auto (Day 14) |
| 21 | Value realization email | Email | Auto (Day 21) |
| 30 | NPS survey | Email | Auto (Day 30) |

**Automation triggers:**
- No login Day 3 → Re-engagement email
- Low usage Day 7 → Help offer email
- High usage Day 7 → Power user tips
- Completed onboarding → Celebration + next steps

### QBR Playbook

#### Pre-QBR (2 weeks before)

| Step | Owner | Deliverable |
|------|-------|-------------|
| Review health metrics | CSM | Health summary |
| Pull usage analytics | CS Ops | Usage report |
| Review support tickets | CSM | Support summary |
| Review success plan progress | CSM | Progress update |
| Identify expansion opportunities | CSM | Expansion proposal |
| Schedule with stakeholders | CSM | Calendar invite |
| Send pre-read agenda | CSM | QBR agenda |

#### QBR Agenda (45-60 minutes)

```
1. BUSINESS ALIGNMENT (10 min)
   → Customer's current priorities
   → Changes since last QBR
   → Success criteria reminder

2. VALUE DELIVERED (15 min)
   → Key metrics and outcomes
   → ROI demonstration
   → Success stories from their team

3. ADOPTION & USAGE (10 min)
   → Product usage highlights
   → Feature adoption
   → Recommendations for improvement

4. ROADMAP PREVIEW (10 min)
   → Upcoming features relevant to them
   → Beta opportunities
   → Feedback on priorities

5. SUCCESS PLAN UPDATE (10 min)
   → Progress against goals
   → Adjustments needed
   → Next quarter objectives

6. NEXT STEPS (5 min)
   → Action items (both sides)
   → Next QBR scheduling
```

#### Post-QBR (within 48 hours)

| Step | Owner | Deliverable |
|------|-------|-------------|
| Send meeting notes | CSM | Email summary |
| Update success plan | CSM | Updated plan |
| Create action items | CSM | Task list |
| Log in CS platform | CSM | QBR record |
| Schedule follow-ups | CSM | Calendar |

### Renewal Playbook

#### T-90 Days: Preparation Phase

| Action | Owner | Output |
|--------|-------|--------|
| Identify renewal date | CS Ops | Renewal report |
| Review health score | CSM | Health assessment |
| Review usage trends | CSM | Usage report |
| Check open issues | CSM | Issue list |
| Assess expansion potential | CSM | Expansion opportunity |
| Assign risk level | CSM | Risk classification |

#### T-60 Days: Engagement Phase

| Action | Owner | Channel |
|--------|-------|---------|
| Renewal intent conversation | CSM | Call |
| Value summary presentation | CSM | QBR/Call |
| Address outstanding issues | CSM | Various |
| Expansion proposal (if ready) | CSM/AE | Call |
| Introduce contract/pricing | CSM | Email |

#### T-30 Days: Execution Phase

| Action | Owner | Output |
|--------|-------|--------|
| Contract sent | Legal/Sales | Contract |
| Negotiate terms (if needed) | CSM/AE | Updated terms |
| Get signature | CSM | Signed contract |
| Process renewal | Ops | Renewed account |
| Celebrate & communicate | CSM | Thank you |

### At-Risk Playbook

**Trigger:** Health score drops below 40 OR cancel signals detected

| Day | Action | Owner | Channel |
|-----|--------|-------|---------|
| 0 | Alert triggered | System | CS Platform |
| 0 | CSM reviews account | CSM | Internal |
| 1 | Outreach to champion | CSM | Email/Call |
| 2 | Internal escalation if no response | CSM | Slack/Meeting |
| 3 | Executive outreach (if needed) | CSM Manager | Email/Call |
| 5 | Discovery call scheduled | CSM | Video |
| 7 | Root cause identified | CSM | Internal doc |
| 10 | Recovery plan created | CSM | Success plan |
| 14 | Recovery plan reviewed with customer | CSM | Video |
| 21 | First recovery checkpoint | CSM | Video |
| 30 | Recovery assessment | CSM | Internal review |

**Escalation triggers:**
- No response in 3 days → Manager involvement
- Health drops below 20 → Executive involvement
- Cancel request received → Save team engaged
- Multiple stakeholder churn → Account review

### Good Playbook Design

```
✓ Clear triggers
  → "When health drops below 40" not "when customer seems unhappy"
  → Objective, measurable

✓ Specific actions
  → "Send renewal summary email using template X"
  → Not "reach out to customer"

✓ Defined ownership
  → Every step has an owner
  → No ambiguity

✓ Realistic timelines
  → Based on actual execution data
  → Buffer for delays

✓ Exit criteria
  → How do we know we're done?
  → What does success look like?

✓ Built-in automation
  → Emails that can be templatized
  → Triggers that can be automated
```

### Bad Playbook Design

```
✗ Vague triggers
  → "When customer is at risk"
  → No objective criteria

✗ Generic steps
  → "Check in with customer"
  → No specific action

✗ No ownership
  → "Team should review"
  → No individual accountability

✗ Unrealistic timelines
  → 15 steps in first week
  → Guaranteed non-compliance

✗ No metrics
  → No way to know if playbook works
  → No improvement possible

✗ Static
  → Written once, never updated
  → Doesn't reflect reality
```

### Playbook Automation

| Manual Step | Automation Opportunity |
|-------------|----------------------|
| Send welcome email | Triggered email on close |
| Schedule kickoff | Calendly/self-scheduling link |
| Send QBR pre-read | Automated email T-7 days |
| Send renewal notice | Triggered email T-90 days |
| Health score alert | Automated Slack notification |
| Create renewal task | Auto-task at T-90 |
| NPS survey | Automated at lifecycle stage |
| Usage report | Auto-generated weekly |

### Playbook Compliance Tracking

| Metric | Target | Review Frequency |
|--------|--------|------------------|
| Onboarding completion rate | >90% | Weekly |
| QBR completion rate | >85% | Monthly |
| Renewal playbook adherence | >90% | Weekly |
| Average playbook completion time | Within SLA | Monthly |
| Steps skipped rate | <10% | Monthly |

### Playbook Review Cadence

| Playbook Type | Review Frequency | Owner |
|---------------|------------------|-------|
| Lifecycle playbooks | Quarterly | CS Ops |
| Intervention playbooks | Monthly | CS Director |
| Operational playbooks | Quarterly | CS Ops |
| All playbooks (major) | Annually | VP CS |

### Anti-Patterns

- **Shelf-ware playbooks** — Created but not used
- **Too many playbooks** — 50 playbooks, none followed
- **No automation** — All manual, doesn't scale
- **No compliance tracking** — Don't know if followed
- **Never updated** — Created 2 years ago, still in use
- **Copy-paste from blog** — Not customized for your business
- **Missing escalation paths** — No guidance when stuck
- **No templates** — CSMs create everything from scratch
