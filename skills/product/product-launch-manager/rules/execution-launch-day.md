---
title: Launch Day Execution
impact: CRITICAL
tags: execution, launch-day, war-room, operations
---

## Launch Day Execution

**Impact: CRITICAL**

Launch day is the culmination of weeks of preparation. Execute with precision through clear runbooks, war rooms, and real-time coordination.

### Launch Day Timeline Template

```
LAUNCH DAY SCHEDULE (Tier 1/2)
══════════════════════════════

06:00  War room opens, monitoring begins
06:30  Engineering: Final deployment verification
07:00  PR embargo lifts, press coverage begins
08:00  Blog post goes live
08:30  Marketing: Social media campaign starts
09:00  Email campaign sends
09:30  In-app notifications enabled
10:00  Sales team notified to begin outreach
10:30  First status check (all teams)
12:00  Midday status check
14:00  Afternoon status check
16:00  End-of-day status check
18:00  War room closes (or as needed)
T+1    Morning debrief, overnight monitoring review
```

### War Room Setup

**Virtual War Room (Slack/Teams):**

```
#launch-war-room
├── Purpose: Real-time coordination
├── Who: Core launch team + on-call
├── Rules:
│   ├── All issues posted here immediately
│   ├── Use threads for discussion
│   ├── Pin critical updates
│   └── No side conversations
│
├── Pinned Messages:
│   ├── Launch runbook link
│   ├── Escalation contacts
│   ├── Status page link
│   └── Rollback command
```

**Physical War Room (if applicable):**

| Station | Owner | Equipment |
|---------|-------|-----------|
| Command | PM | Screens for metrics, Slack |
| Engineering | Eng Lead | Deployment dashboards |
| Support | Support Lead | Ticket queue, live chat |
| Marketing | PMM | Social monitoring |
| Executive | Exec Sponsor | Escalation decisions |

### Launch Runbook Template

```markdown
# [Feature] Launch Runbook

## Pre-Launch Checklist (T-1 hour)
□ All deployments complete
□ Feature flags ready to enable
□ Monitoring dashboards open
□ On-call engineers confirmed
□ Support team briefed
□ Rollback plan reviewed

## Launch Sequence
| Time | Action | Owner | Verify |
|------|--------|-------|--------|
| 08:00 | Enable feature flag | @eng-lead | [link] |
| 08:05 | Verify metrics baseline | @pm | [link] |
| 08:10 | Publish blog post | @pmm | [link] |
| 08:15 | Verify blog live | @pmm | [link] |
| 08:30 | Send email campaign | @pmm | [link] |
| 08:35 | Verify emails sending | @pmm | [link] |
| 09:00 | Enable in-app notification | @eng | [link] |
| 09:05 | Post to social channels | @pmm | [links] |
| 09:30 | First health check | @all | [checklist] |

## Health Check Protocol
Every 2 hours, verify:
□ Error rate < 0.1%
□ Latency p95 < 200ms
□ Support tickets < threshold
□ Social sentiment neutral/positive
□ Feature adoption tracking

## Escalation Matrix
| Issue Type | First Contact | Escalate To | SLA |
|------------|---------------|-------------|-----|
| P0 (system down) | @eng-oncall | @eng-lead | 5 min |
| P1 (degraded) | @eng-oncall | @eng-lead | 15 min |
| Support spike | @support-lead | @pm | 30 min |
| PR issue | @pmm | @comms-lead | 15 min |
| Exec escalation | @pm | @exec-sponsor | Immediate |

## Rollback Procedure
If rollback needed:
1. PM announces in #launch-war-room
2. Eng lead confirms with "ROLLBACK CONFIRMED"
3. Execute: `./scripts/rollback-feature.sh`
4. Verify rollback complete
5. PM notifies stakeholders
6. Marketing pauses campaigns
7. Support sends holding response

## Emergency Contacts
| Role | Name | Phone | Slack |
|------|------|-------|-------|
| PM | [Name] | [Phone] | @handle |
| Eng Lead | [Name] | [Phone] | @handle |
| Exec Sponsor | [Name] | [Phone] | @handle |
```

### Good Example: Smooth Launch Execution

```markdown
## Launch Day Log: Enterprise SSO

**08:00** - Feature flag enabled. All systems green.
**08:05** - Baseline metrics captured. Error rate 0.02%.
**08:10** - Blog published. [link verified]
**08:32** - Email campaign started. 50K recipients.
**09:00** - In-app notification live.
**09:15** - First support ticket: user confused by setup.
           FAQ updated. Not escalated.
**09:30** - Health check: All green.
           - Error rate: 0.03%
           - First 10 SSO setups successful
           - Social sentiment: Positive
**10:30** - 47 SSO setups completed (target: 30).
**12:00** - Midday check: All green.
           - Error rate: 0.02%
           - 89 SSO setups
           - 3 support tickets (all resolved)
**14:00** - Press coverage starting to appear.
**16:00** - EOD check:
           - 156 SSO setups (target: 100)
           - 0 P0/P1 incidents
           - 8 support tickets (all resolved)
           - NPS from early users: 62
**17:00** - War room closed. Overnight monitoring enabled.

**Status: SUCCESSFUL LAUNCH**
```

### Bad Example: Chaotic Launch

```markdown
## Launch Day Disaster: Widget 2.0

**08:00** - Feature supposed to launch. Deployment stuck.
**08:15** - Blog post goes live anyway (premature).
**08:20** - Customers seeing "feature not found" errors.
**08:30** - Twitter complaints start.
**08:45** - Deployment finally completes.
**09:00** - Email sends to customers who already saw errors.
**09:15** - Support queue at 50 tickets, team not briefed.
**09:30** - No health check performed. PM in meetings.
**10:00** - Exec asks for status. No one has update.
**11:00** - Error rate discovered at 5% (limit was 0.1%).
**11:30** - Rollback decision debated for 30 minutes.
**12:00** - Rollback executed. Customers confused.
**12:30** - Blog post still live describing feature.
**14:00** - Press article published about "botched launch."

**Root Causes:**
- No deployment verification step
- No coordination between eng and marketing
- No war room or communication channel
- No health check protocol
- No clear rollback decision authority
```

### Real-Time Decision Framework

| Signal | Threshold | Action |
|--------|-----------|--------|
| Error rate | > 1% | Investigate immediately |
| Error rate | > 5% | Rollback consideration |
| P0 incident | Any | Rollback unless fix < 15 min |
| Support volume | > 5x normal | Pause marketing, assess |
| Negative press | Major outlet | Exec notification |
| Security issue | Any | Immediate rollback |

### Communication Templates

**War Room Status Update:**
```
🟢 STATUS CHECK [10:30]

Metrics:
- Error rate: 0.03% (limit: 0.1%)
- Adoption: 47 setups (target: 30)
- Support: 3 tickets (all resolved)

No blockers. Next check: 12:00.
```

**Escalation Message:**
```
🟡 ESCALATION [11:15]

Issue: Error rate at 0.8%, trending up
Impact: ~50 users affected
Cause: Database connection pooling
Action: Eng investigating, ETA 15 min
Decision needed: None yet

Next update: 11:30 or sooner if change
```

**Rollback Announcement:**
```
🔴 ROLLBACK INITIATED [11:45]

Decision: Rollback due to error rate > 2%
Status: In progress
ETA: 15 minutes

Actions:
- @marketing: Pause all campaigns
- @support: Send holding response template
- @eng: Execute rollback
- @pm: Notify exec sponsor

Will confirm completion.
```

### Post-Launch Day Checklist

```
End of Day:
□ Final metrics captured
□ All incidents documented
□ Support queue cleared or handed off
□ Marketing campaigns assessed
□ Overnight monitoring confirmed
□ Key wins/issues summarized for exec
□ War room closed or transitioned

Day 2 Morning:
□ Overnight alerts reviewed
□ Metrics trend assessed
□ Support volume checked
□ Social sentiment reviewed
□ Quick wins identified
□ Follow-up actions assigned
```

### Anti-Patterns

- **No runbook** — Making it up as you go
- **No war room** — Communication scattered across channels
- **Premature publishing** — Marketing goes before engineering confirms
- **No health checks** — Assuming green until someone complains
- **Unclear rollback authority** — Debate during crisis
- **PM unavailable** — Captain leaves the ship
- **No escalation path** — Issues fester
- **Launch and leave** — War room closes at 5pm sharp
