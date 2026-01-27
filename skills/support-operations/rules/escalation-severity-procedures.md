---
title: Escalation Procedures & Severity Definitions
impact: CRITICAL
tags: escalation, severity, incident, on-call, war-room, crisis
---

## Escalation Procedures & Severity Definitions

**Impact: CRITICAL**

Clear escalation procedures ensure critical issues reach the right people fast. Vague severity definitions lead to under-escalation (customers suffer) or over-escalation (alert fatigue). Get this right and crises become manageable incidents.

### Severity Level Definitions

| Severity | Name | Definition | Examples |
|----------|------|------------|----------|
| **SEV1** | Critical | Complete system outage, data loss, security breach | Production down, data breach, complete loss of service |
| **SEV2** | High | Major feature broken for many users | Core workflow blocked, payment processing down |
| **SEV3** | Medium | Feature degraded or broken for some users | Slow performance, partial functionality |
| **SEV4** | Low | Minor issue, workaround available | UI bug, cosmetic issue, edge case |
| **SEV5** | Minimal | Enhancement request, how-to question | Feature request, documentation question |

### Severity Decision Matrix

```
                    ┌─────────────────────────────────────┐
                    │            USERS AFFECTED           │
                    ├──────────┬──────────┬───────────────┤
                    │ One User │ Multiple │ All Users     │
┌───────────────────┼──────────┼──────────┼───────────────┤
│ Complete Block    │   SEV3   │   SEV2   │     SEV1      │
├───────────────────┼──────────┼──────────┼───────────────┤
│ Major Impairment  │   SEV4   │   SEV3   │     SEV2      │
├───────────────────┼──────────┼──────────┼───────────────┤
│ Minor Impairment  │   SEV5   │   SEV4   │     SEV3      │
└───────────────────┴──────────┴──────────┴───────────────┘
```

### Escalation Paths by Severity

| Severity | First Response | 30 min | 1 hour | 2 hours | 4 hours |
|----------|---------------|--------|--------|---------|---------|
| **SEV1** | On-call engineer | VP Eng | CTO | CEO | Board update |
| **SEV2** | L3 engineer | Eng Manager | VP Eng | CTO | - |
| **SEV3** | L2 specialist | L3 engineer | Eng Manager | - | - |
| **SEV4** | L1 agent | L2 specialist | - | - | - |
| **SEV5** | L1 agent | - | - | - | - |

### Escalation Response Requirements

| Severity | Response SLA | Update Frequency | Communication |
|----------|--------------|------------------|---------------|
| **SEV1** | 15 minutes | Every 15 minutes | Status page, proactive email, exec bridge |
| **SEV2** | 30 minutes | Every 30 minutes | Affected users, internal Slack |
| **SEV3** | 1 hour | Every 2 hours | Ticket updates |
| **SEV4** | 4 hours | Every 8 hours | Ticket updates |
| **SEV5** | 8 hours | At resolution | Ticket updates |

### Good Escalation Practices

```
✓ Clear severity criteria
  → Written definitions with examples
  → Decision tree for ambiguous cases
  → Regular calibration across team

✓ No-blame escalation culture
  → Better to escalate than miss
  → Learning from near-misses
  → Celebrate good catches

✓ Context travels with escalation
  → Full ticket history
  → Troubleshooting already done
  → Customer impact documented

✓ Defined communication templates
  → Internal update format
  → Customer communication format
  → Status page update process

✓ Post-incident review
  → Every SEV1/SEV2 gets review
  → Blameless root cause analysis
  → Action items tracked to completion
```

### Bad Escalation Practices

```
✗ Escalation as punishment
  → "You should have handled this"
  → Agents afraid to escalate

✗ No severity definitions
  → Everything is SEV1 or nothing is
  → Inconsistent customer experience

✗ Escalation black holes
  → Tickets go up, never come back
  → Engineering ignores queue

✗ Context-free handoffs
  → "It's broken" with no details
  → Customer re-explains 3 times

✗ No update cadence
  → Customer in the dark
  → Internal teams unaware

✗ Skip-level escalations
  → Everyone emails the CEO
  → Process bypassed
```

### On-Call Structure

| Tier | Coverage | Responsibilities |
|------|----------|------------------|
| **Primary On-Call** | 24/7 | First responder for all alerts |
| **Secondary On-Call** | 24/7 | Backup if primary unreachable |
| **Manager On-Call** | 24/7 | Escalation point, decision maker |
| **Executive On-Call** | 24/7 | Major incident communication |

### On-Call Rotation Best Practices

```
Rotation Schedule:
├── 1-week rotations (not longer)
├── Minimum 2 people per rotation
├── Time zone coverage consideration
├── Holidays covered and compensated
└── Handoff at consistent time (e.g., Monday 9am)

On-Call Expectations:
├── Respond to page within 5 minutes
├── Acknowledge or escalate within 15 minutes
├── Laptop and internet access required
├── Not impaired (alcohol, etc.)
└── Backup coverage for personal conflicts
```

### Incident Command Structure (SEV1/SEV2)

| Role | Responsibility | Example Actions |
|------|----------------|-----------------|
| **Incident Commander** | Overall coordination | Runs bridge, makes decisions |
| **Technical Lead** | Technical investigation | Debugging, deploying fixes |
| **Communications Lead** | Updates stakeholders | Status page, customer emails |
| **Scribe** | Documentation | Timeline, actions, decisions |
| **Subject Matter Experts** | Specific expertise | Called in as needed |

### War Room Protocol (SEV1)

```
Initiation (0-15 minutes):
□ Page on-call and backup
□ Open incident bridge (Zoom/Slack)
□ Assign Incident Commander
□ Initial impact assessment
□ Post to status page

Active Incident:
□ Update status page every 15 minutes
□ Scribe maintains timeline
□ IC coordinates investigation
□ Parallel workstreams if needed
□ All changes announced before made

Resolution:
□ Confirm customer impact resolved
□ Update status page to resolved
□ Send all-clear internally
□ Draft customer communication
□ Schedule post-incident review
```

### Customer Communication Templates

**SEV1 - Initial Notification:**
```
Subject: [Service Name] - Service Disruption

We are currently experiencing an issue affecting [description].

Impact: [What customers are experiencing]
Status: Our team is actively investigating
Next Update: Within 30 minutes

We apologize for the inconvenience and will keep you updated.

[Link to status page]
```

**SEV1 - Resolution:**
```
Subject: [Service Name] - Issue Resolved

The issue affecting [description] has been resolved.

Duration: [Start time] to [End time]
Impact: [What was affected]
Resolution: [Brief explanation]

We apologize for any inconvenience caused. A detailed
post-incident report will be shared within 48 hours.

[Link to status page]
```

### Internal Escalation Template

```
## Escalation Summary

**Severity:** [SEV1/2/3/4]
**Time Detected:** [Timestamp]
**Escalated By:** [Name]
**Escalated To:** [Name/Team]

### Issue Description
[2-3 sentences describing the problem]

### Customer Impact
- Affected customers: [Number or percentage]
- Impact type: [Outage/Degradation/Error]
- Customer-facing symptoms: [What they're seeing]

### Investigation So Far
- [Step 1] → [Result]
- [Step 2] → [Result]
- [Current hypothesis]

### Immediate Actions Needed
1. [Action 1]
2. [Action 2]

### Communication Status
- Status page: [Updated/Pending]
- Customer notification: [Sent/Pending/Not needed]
- Internal channel: [Posted in #channel]
```

### Post-Incident Review Template

```
## Post-Incident Review: [Incident Title]

**Date:** [Date]
**Duration:** [Start to End]
**Severity:** [SEV level]
**Incident Commander:** [Name]

### Summary
[1-2 paragraph summary of what happened]

### Timeline
- [HH:MM] First customer report
- [HH:MM] On-call paged
- [HH:MM] Incident declared
- [HH:MM] Root cause identified
- [HH:MM] Fix deployed
- [HH:MM] Customer impact resolved

### Impact
- Customers affected: [Number]
- Duration of impact: [Time]
- Revenue impact: [If applicable]
- SLA impact: [Breaches if any]

### Root Cause
[Technical explanation of what went wrong]

### What Went Well
- [Positive 1]
- [Positive 2]

### What Could Be Improved
- [Improvement 1]
- [Improvement 2]

### Action Items
| Action | Owner | Due Date | Status |
|--------|-------|----------|--------|
| [Action 1] | [Name] | [Date] | Open |
| [Action 2] | [Name] | [Date] | Open |
```

### Anti-Patterns

- **Severity inflation** — Everything is SEV1, real emergencies ignored
- **Escalation avoidance** — Agents sit on critical issues too long
- **Hero culture** — One person handles all incidents alone
- **No post-mortems** — Same issues repeat without learning
- **Customer last** — Internal comms before customer updates
- **War room theater** — 50 people on a call, 3 doing work
- **Blame-focused reviews** — "Who did this?" instead of "How do we prevent?"
- **On-call burnout** — Same people always on call, no rotation
