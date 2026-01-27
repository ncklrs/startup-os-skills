---
title: Process Automation & Workflows
impact: HIGH
tags: automation, workflow, process, efficiency, salesforce
---

## Process Automation & Workflows

**Impact: HIGH**

The best automation makes the right thing easy and the wrong thing hard. Automate to enable reps, not to police them.

### Automation ROI Framework

Before automating, calculate the value:

```
Automation ROI = (Time Saved × Frequency × Hourly Cost) - Build Cost

Example: Auto-create follow-up task after demo
- Time saved: 2 min per demo
- Frequency: 200 demos/month
- Hourly cost: $50/hr
- Build cost: 2 hours

Monthly ROI = (2/60 × 200 × $50) - (2 × $50) = $333 - $100 = $233/month first month
             (2/60 × 200 × $50) = $333/month ongoing
```

### Automation Priority Matrix

| Impact | Effort Low | Effort High |
|--------|------------|-------------|
| **High Impact** | DO NOW | PLAN |
| **Low Impact** | AUTOMATE LATER | DON'T DO |

**High Impact / Low Effort (Do Now):**
- Auto-assign leads by territory
- Task creation on stage change
- Notification on deal close
- Field updates on record creation

**High Impact / High Effort (Plan):**
- Complex approval workflows
- Multi-system integrations
- AI-powered lead scoring
- Automated forecasting

### Common Automation Patterns

#### 1. Lead Assignment

```
Trigger: New Lead Created
Conditions:
  - Lead Status = "New"
  - Lead Source != "Manual Entry"
Actions:
  1. Run assignment rules
  2. Create task: "Contact new lead within 5 min"
  3. Send Slack notification to assigned rep
  4. Update Lead Status to "Assigned"
```

#### 2. Stage Change Workflow

```
Trigger: Opportunity Stage Changed
Conditions:
  - Stage changed to "Demo/Evaluation"
Actions:
  1. Create task: "Send demo follow-up" (due +1 day)
  2. Add to Outreach sequence: "Post-Demo Nurture"
  3. Update field: Last_Stage_Change_Date__c = TODAY()
  4. Notify manager if deal size > $100K
```

#### 3. Deal Escalation

```
Trigger: Scheduled (Daily at 8am)
Conditions:
  - Stage = "Proposal" or "Negotiation"
  - Days in stage > 21
  - Amount > $50,000
Actions:
  1. Send email alert to VP Sales
  2. Create Chatter post on record
  3. Add to "At Risk" report
```

### Workflow Decision Tree

```
                    ┌─────────────────┐
                    │ Is this process │
                    │ well-defined?   │
                    └────────┬────────┘
                             │
              ┌──────────────┴──────────────┐
              │ NO                          │ YES
              ▼                             ▼
    ┌─────────────────┐           ┌─────────────────┐
    │ Document process│           │ Does it happen  │
    │ first, then     │           │ frequently?     │
    │ automate        │           │ (>10x/week)     │
    └─────────────────┘           └────────┬────────┘
                                           │
                              ┌────────────┴────────────┐
                              │ NO                      │ YES
                              ▼                         ▼
                    ┌─────────────────┐       ┌─────────────────┐
                    │ Consider manual │       │ Is the logic    │
                    │ process or      │       │ consistent?     │
                    │ simple reminder │       │ (no exceptions) │
                    └─────────────────┘       └────────┬────────┘
                                                       │
                                          ┌────────────┴────────────┐
                                          │ NO                      │ YES
                                          ▼                         ▼
                                ┌─────────────────┐       ┌─────────────────┐
                                │ Build with      │       │ AUTOMATE IT     │
                                │ exception       │       │                 │
                                │ handling        │       │                 │
                                └─────────────────┘       └─────────────────┘
```

### Automation Tools Comparison

| Tool | Best For | Complexity | Cost |
|------|----------|------------|------|
| **Salesforce Flow** | Complex Salesforce automation | High | Included |
| **Process Builder** | Simple field updates (legacy) | Low | Included |
| **Workflow Rules** | Basic notifications (legacy) | Low | Included |
| **Zapier** | Cross-system, no-code | Medium | $$ |
| **Workato** | Enterprise integrations | High | $$$ |
| **Tray.io** | Complex multi-step | High | $$$ |
| **n8n** | Self-hosted, technical team | High | $ |

### Salesforce Flow Best Practices

**Good Flow Design:**
```yaml
Flow Name: Opp_Stage_Change_Handler
Type: Record-Triggered Flow
Object: Opportunity
Trigger: After Update
Entry Conditions:
  - Stage was changed
  - Stage != "Closed Won" AND Stage != "Closed Lost"

Actions:
  1. Decision: Check new stage value
  2. Assignment: Update related fields
  3. Create Records: Generate tasks
  4. Action: Send notifications

Error Handling:
  - Fault connector to error handling subflow
  - Admin notification on failure
  - Transaction rollback on critical errors
```

**Bad Flow Design:**
```yaml
Flow Name: New_Flow_1
Type: Record-Triggered Flow
Object: Opportunity
Trigger: Before Update AND After Update (double triggers!)
Entry Conditions: None (runs on every save!)

Actions:
  - 47 actions in linear sequence
  - No error handling
  - Hardcoded IDs
  - Queries inside loops
```

### Notification Strategy

| Event | Channel | Audience | Urgency |
|-------|---------|----------|---------|
| Deal Closed Won >$100K | Slack #wins | Whole company | Immediate |
| Lead not contacted in 5 min | Slack DM | Assigned rep | Immediate |
| Opp stage changed | Email | Rep + Manager | Daily digest |
| Forecast commit change | Email | VP Sales | Real-time |
| Opp past close date | In-app | Rep | On login |

### Automation Documentation Template

```markdown
## Automation: [Name]
**Owner:** [Sales Ops team member]
**Created:** [Date]
**Last Modified:** [Date]

### Purpose
[What business problem does this solve?]

### Trigger
[What initiates this automation?]

### Logic
[Step-by-step what happens]

### Affected Fields/Records
[What gets created/updated]

### Error Handling
[What happens when it fails]

### Testing Notes
[How to test this automation]

### Known Limitations
[Edge cases or exceptions]
```

### Anti-Patterns

- **Automation spaghetti** — No documentation, impossible to debug
- **Over-notification** — Alert fatigue kills effectiveness
- **No testing environment** — Automations go straight to production
- **Hardcoded values** — IDs, names, amounts embedded in logic
- **No error handling** — Silent failures corrupt data
- **Automating bad processes** — Making mistakes faster
- **Single point of failure** — Only one person knows how it works
- **No audit trail** — Can't trace what automation changed what
