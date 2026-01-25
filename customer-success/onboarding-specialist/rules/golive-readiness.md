---
title: Go-Live Readiness & Launch Success
impact: HIGH
tags: go-live, launch, readiness, pilot, rollout
---

## Go-Live Readiness & Launch Success

**Impact: HIGH**

Go-live is the moment of truth in onboarding. A successful launch builds confidence and momentum; a failed launch can permanently damage adoption. Only 30% of software implementations achieve their original go-live date. Planning and readiness assessment make the difference.

### Go-Live Readiness Stages

```
PILOT → READINESS → GO-LIVE → STABILIZATION → OPTIMIZATION
  ↓         ↓          ↓           ↓              ↓
 Test    Validate   Launch     Support        Improve
 Small    All       Full       Issues         Expand
 Group   Criteria   Rollout    Resolution     Adoption
```

### Pilot Program Framework

| Aspect | Recommendation | Rationale |
|--------|----------------|-----------|
| **Duration** | 1-2 weeks | Enough time to find issues |
| **Size** | 5-15% of users | Representative but contained |
| **Selection** | Mix of enthusiasts + skeptics | Balanced feedback |
| **Scope** | Core workflows only | Focus on critical path |
| **Support** | High-touch | Capture all feedback |
| **Success criteria** | Defined upfront | Clear go/no-go decision |

### Pilot User Selection Criteria

```
✓ Good pilot candidates:
  → Engaged and available during pilot period
  → Represent different user types/roles
  → Willing to provide feedback
  → Tech-comfortable but not just power users
  → Include some skeptics (valuable feedback)

✗ Avoid for pilot:
  → VIPs who can't tolerate issues
  → Users on vacation or busy with other projects
  → Only enthusiasts (biased feedback)
  → Critical path users if failure = business impact
```

### Go-Live Readiness Checklist

```
## Go-Live Readiness Checklist: [Customer Name]
**Target Go-Live Date:** [Date]
**Assessment Date:** [Date]
**Status:** Ready / Not Ready / Conditionally Ready

### Technical Readiness
□ Core configuration complete and tested
□ Integrations working in production
□ Data migration complete and validated
□ User accounts provisioned
□ SSO/authentication functioning
□ Performance tested under expected load
□ Backup and recovery validated
□ Security review passed

### Operational Readiness
□ Admin team trained and certified
□ End user training completed (>80% completion)
□ Support procedures documented
□ Escalation paths defined
□ Internal help resources available
□ Change management communications sent
□ User guides and documentation accessible

### Business Readiness
□ Success criteria defined and measurable
□ Baseline metrics captured
□ Executive sponsor briefed
□ Stakeholders aligned on go-live date
□ Rollback plan documented (if needed)
□ Go-live communication drafted

### Support Readiness
□ Hypercare support plan in place
□ Known issues documented with workarounds
□ War room/rapid response team identified
□ Vendor support escalation configured
□ Monitoring and alerting active

### Final Approvals
□ Customer project manager: _______________
□ Vendor project manager: _______________
□ Customer executive sponsor: _______________
□ Technical lead: _______________
```

### Good Go-Live Practices

```
✓ Phased rollout
  → Start with pilot group
  → Expand in waves
  → Learn and adjust between phases

✓ Hypercare period
  → Increased support coverage
  → Rapid response to issues
  → Dedicated resources

✓ Clear communication
  → What's changing, when, why
  → Where to get help
  → Set expectations

✓ War room readiness
  → Cross-functional team available
  → Decision authority present
  → Communication channels open

✓ Success celebration
  → Acknowledge the milestone
  → Recognize contributors
  → Build momentum
```

### Bad Go-Live Practices

```
✗ Big bang without pilot
  → All users at once, no testing
  → Problems hit everyone simultaneously

✗ No hypercare
  → Normal support levels
  → Issues queue up, frustration builds

✗ Silent launch
  → Users discover changes unexpectedly
  → No preparation, resistance increases

✗ Go-live on Friday
  → Weekend for issues to compound
  → No support available

✗ Premature declaration
  → "We're live!" with critical issues
  → Users lose trust immediately
```

### Rollout Strategy Options

| Strategy | Description | Best For | Risk Level |
|----------|-------------|----------|------------|
| **Big Bang** | All users at once | Simple, low risk | High |
| **Phased by Group** | Department by department | Large orgs | Medium |
| **Phased by Feature** | Core first, expand | Complex products | Low |
| **Parallel Running** | Old + new simultaneously | Critical systems | Low |
| **Pilot + Expand** | Small group first | Most implementations | Low |

### Launch Communication Template

```
## [Product] Launch Communication

### Pre-Launch (1 week before)
Subject: [Product] Going Live on [Date] - What You Need to Know

Hi Team,

On [Date], we're launching [Product] to [improve X/replace Y/enable Z].

**What's Changing:**
- [Change 1]
- [Change 2]

**What You Need to Do:**
- [ ] Complete training by [Date] - [Link]
- [ ] Review quick start guide - [Link]
- [ ] Test your login - [Link]

**Getting Help:**
- Help desk: [Contact]
- Resources: [Link]
- FAQ: [Link]

Questions? Reply to this email.

---

### Launch Day
Subject: [Product] is Now Live!

Hi Team,

[Product] is now live and ready for you to use!

**Quick Start:**
1. Log in at [URL]
2. [First step to take]
3. [Second step to take]

**Need Help?**
- Quick start guide: [Link]
- Live support: [Contact] (extra coverage this week)
- Help center: [Link]

**Report Issues:**
- Email: [support@...]
- Slack: #[channel]

Let's make this a success!

---

### Post-Launch (3 days after)
Subject: [Product] Launch Update - Tips & Support

Hi Team,

We're 3 days into [Product] - here's what you need to know:

**Quick Tips Based on Your Feedback:**
- Tip 1: [Common question answer]
- Tip 2: [Helpful shortcut]

**Known Issues:**
- [Issue 1]: [Workaround]
- [Issue 2]: Being fixed, expected [date]

**Your Feedback Matters:**
We're collecting feedback to improve your experience.
[Feedback survey link]

Keep the questions coming - we're here to help.
```

### Hypercare Plan Template

```
## Hypercare Plan: [Customer Name]

**Duration:** [2 weeks recommended]
**Start Date:** [Go-live date]
**End Date:** [Date]

### Support Coverage
| Time | Coverage | Channel |
|------|----------|---------|
| Business hours | Extended team | All channels |
| After hours | On-call rotation | Email, urgent phone |
| Weekend | On-call | Emergency only |

### Response Times (During Hypercare)
| Severity | Definition | Response | Resolution |
|----------|------------|----------|------------|
| Critical | System down | 15 min | 2 hours |
| High | Major feature broken | 1 hour | 4 hours |
| Medium | Workaround available | 4 hours | 24 hours |
| Low | Minor issue | 24 hours | 72 hours |

### Daily Sync
- **Time:** [Time] daily
- **Participants:** [Customer + Vendor leads]
- **Agenda:** Issues, trends, decisions
- **Duration:** 15-30 min

### Issue Tracking
- Log all issues in [system]
- Categorize by severity and type
- Daily summary report
- Trend analysis weekly

### Exit Criteria
Hypercare ends when:
□ No critical/high issues open for 48+ hours
□ Issue volume trending down
□ Customer confirms stability
□ Handoff to standard support complete
```

### Go-Live Success Metrics

| Metric | Target | Measurement |
|--------|--------|-------------|
| **User activation** | >80% in week 1 | Users logged in / Total |
| **Feature adoption** | >60% using core | Core feature usage |
| **Issue volume** | Decreasing trend | Support tickets daily |
| **Critical issues** | 0 unresolved | P1 ticket count |
| **User satisfaction** | >4/5 | Quick pulse survey |
| **System availability** | >99.9% | Uptime monitoring |

### Rollback Criteria & Plan

```
## Rollback Decision Framework

### Automatic Rollback Triggers
- System availability <95% for >2 hours
- Critical data loss or corruption
- Security breach

### Evaluation Triggers (Consider Rollback)
- >50% of users unable to complete core workflow
- Critical business process blocked
- Executive sponsor requests review

### Rollback Plan
1. **Decision authority:** [Name] with [backup name]
2. **Communication:** Draft ready, send within 30 min
3. **Technical steps:** [Documented procedure]
4. **User impact:** [What changes for users]
5. **Recovery timeline:** [How long to restore]
6. **Post-mortem:** Within 48 hours of rollback
```

### Post-Go-Live Review Template

```
## Go-Live Review: [Customer Name]

**Go-Live Date:** [Date]
**Review Date:** [Date, ~2 weeks post]

### Metrics Summary
| Metric | Target | Actual | Status |
|--------|--------|--------|--------|
| On-time | [Date] | [Date] | ✅/❌ |
| User adoption | 80% | X% | ✅/❌ |
| Critical issues | 0 | X | ✅/❌ |
| User satisfaction | 4/5 | X/5 | ✅/❌ |

### What Went Well
- [Success 1]
- [Success 2]
- [Success 3]

### What Could Improve
- [Improvement 1] - [Action]
- [Improvement 2] - [Action]

### Lessons Learned
- [Lesson 1]
- [Lesson 2]

### Next Steps
- [ ] Transition to ongoing success
- [ ] Schedule 30-day review
- [ ] Identify optimization opportunities
- [ ] Gather success story content
```

### Anti-Patterns

- **Go-live by date, not readiness** — Calendar over quality
- **Skipping pilot** — No validation before full rollout
- **Normal support levels at launch** — Users feel abandoned
- **No rollback plan** — Committed with no exit
- **Weekend launches** — No support when issues arise
- **Declaring success prematurely** — Before stabilization
- **No post-launch review** — Same mistakes next time
- **Disappearing after go-live** — Onboarding is not adoption
