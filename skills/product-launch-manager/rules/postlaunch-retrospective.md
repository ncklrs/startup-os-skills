---
title: Launch Retrospectives
impact: HIGH
tags: postlaunch, retrospective, learning, improvement
---

## Launch Retrospectives

**Impact: HIGH**

Every launch is a learning opportunity. Structured retrospectives turn experience into institutional knowledge.

### Retrospective Timeline

| Launch Tier | Retro Timing | Duration | Participants |
|-------------|--------------|----------|--------------|
| **Tier 1** | T+2 weeks | 90 min | Full cross-functional team |
| **Tier 2** | T+1 week | 60 min | Core launch team |
| **Tier 3** | T+1 week | 30 min | PM + key contributors |
| **Tier 4** | Optional | 15 min | PM async doc |

### Retrospective Framework

```
THE 4L RETROSPECTIVE
════════════════════

┌─────────────────┬─────────────────┐
│    LIKED        │    LEARNED      │
│                 │                 │
│  What went well │  New insights   │
│  that we should │  and knowledge  │
│  repeat         │  gained         │
│                 │                 │
├─────────────────┼─────────────────┤
│    LACKED       │    LONGED FOR   │
│                 │                 │
│  What was       │  What we wish   │
│  missing or     │  we had done    │
│  insufficient   │  differently    │
│                 │                 │
└─────────────────┴─────────────────┘
```

### Retrospective Agenda Template

```markdown
## Launch Retrospective: [Feature Name]

**Date:** [Date]
**Facilitator:** [Name]
**Attendees:** [List]

### Agenda (60-90 minutes)

1. **Context Setting** (5 min)
   - Launch goals recap
   - Success criteria recap
   - Key metrics summary

2. **Success Criteria Review** (10 min)
   - Did we hit our targets?
   - What do the numbers tell us?

3. **Timeline Review** (10 min)
   - Walk through major milestones
   - Where did we get ahead/behind?

4. **4Ls Exercise** (25 min)
   - 5 min silent brainstorming
   - 20 min group discussion

5. **Action Items** (15 min)
   - What will we do differently?
   - Who owns each action?

6. **Kudos** (5 min)
   - Recognize contributions
```

### Good Example: Comprehensive Retrospective

```markdown
## Launch Retrospective: Enterprise SSO

**Date:** October 28, 2024
**Facilitator:** Sarah Chen (PM)
**Attendees:** Mike (PMM), Priya (Eng), Tom (Sales), Lisa (Support)

### Success Criteria Results

| Metric | Target | Actual | Status |
|--------|--------|--------|--------|
| SSO setups (30d) | 200 | 390 | EXCEEDED |
| Active SSO users | 5,000 | 9,500 | EXCEEDED |
| Error rate | < 0.1% | 0.02% | MET |
| Setup NPS | > 50 | 64 | EXCEEDED |
| Pipeline influenced | $500K | $620K | EXCEEDED |

**Overall: SUCCESSFUL LAUNCH**

### Liked (What went well)

1. **Cross-functional coordination**
   - Weekly syncs kept everyone aligned
   - Slack channel was invaluable for real-time updates
   - "Best coordinated launch I've been part of" - Tom

2. **Beta program**
   - Caught the Azure AD issue before GA
   - Customer quotes ready for launch day
   - Created internal champions

3. **Enablement materials**
   - Sales one-pager was "actually useful" (Tom's words)
   - Support troubleshooting guide prevented escalations
   - 90% of support tickets resolved with existing docs

4. **Launch day execution**
   - War room worked smoothly
   - No deployment issues
   - Marketing timing was perfect

### Learned (New insights)

1. **Beta cohort diversity matters**
   - Almost missed Azure AD edge case
   - Need to ensure geographic + IdP diversity

2. **Sales enablement timing**
   - 2 weeks before launch was right
   - Too early = forgotten, too late = unprepared

3. **In-app messaging impact**
   - In-app notification drove 40% of setups
   - Higher than email (25%) or blog (15%)

4. **Enterprise sales cycle**
   - Feature announcement → close takes 45-60 days
   - Should set 90-day pipeline targets, not 30-day

### Lacked (What was missing)

1. **International readiness**
   - No GDPR-specific documentation at launch
   - EU customers asked questions we couldn't answer

2. **Partner enablement**
   - Okta partnership team found out from blog post
   - Should have briefed integration partners

3. **Video content**
   - Multiple requests for setup walkthrough video
   - Added friction for visual learners

4. **Customer success playbook**
   - CS team wasn't sure how to position SSO in renewals
   - Created after launch, should have been ready

### Longed For (What we'd do differently)

1. **Earlier executive alignment**
   - Tier decision debated for 2 weeks
   - Should lock this at kickoff

2. **Longer beta for enterprise features**
   - 4 weeks felt rushed for enterprise IT teams
   - 6-8 weeks for enterprise-focused features

3. **Pre-written FAQ expansion**
   - First week support was reactive
   - Should anticipate more edge case questions

4. **Competitive response plan**
   - Competitor launched similar feature 2 weeks later
   - Were caught flat-footed on positioning

### Action Items

| Action | Owner | Due Date | Priority |
|--------|-------|----------|----------|
| Add GDPR docs to launch checklist | Lisa | Nov 5 | High |
| Create partner briefing template | Mike | Nov 10 | High |
| Add video to enablement checklist | Mike | Nov 10 | Medium |
| CS playbook required for Tier 1-2 | Sarah | Nov 15 | High |
| Extend enterprise beta standard to 6 weeks | Sarah | Next launch | Medium |
| Add competitive response to launch brief | Mike | Next launch | Medium |

### Kudos

- **Priya:** Flawless deployment, zero incidents
- **Tom:** Closed first SSO deal in 3 weeks
- **Lisa:** Support NPS highest ever for a launch
- **Mike:** Blog post generated 3 press pickups
- **Everyone:** Best cross-functional collab in 2024
```

### Bad Example: Superficial Retrospective

```markdown
## Retro: Widget 2.0

**Date:** Friday 5pm (30 min scheduled, 15 min actual)
**Who showed up:** PM, 1 engineer

### What happened:
- We launched
- Some bugs
- Customers complained

### What we learned:
- Test more
- Communicate better

### Action items:
- None assigned

**Why This Failed:**
- Rushed timing (Friday 5pm)
- Missing key stakeholders
- No metrics reviewed
- Vague insights ("communicate better")
- No ownership of actions
- Will repeat same mistakes
```

### Retrospective Facilitation Tips

**Before:**
```
□ Schedule 2+ weeks in advance (calendars fill up)
□ Send pre-work: metrics summary, timeline, 4Ls template
□ Book 30 min buffer after for overflow
□ Ensure all key roles can attend
□ Prepare metrics dashboard
```

**During:**
```
□ Start with metrics (ground the conversation in data)
□ Use silent brainstorming (prevents groupthink)
□ Timebox each section
□ Capture everything (assign note-taker)
□ End with action items + owners + dates
□ Always include kudos
```

**After:**
```
□ Send notes within 24 hours
□ Add action items to project tracker
□ Follow up on action items at next team meeting
□ Archive retro for future reference
```

### Retrospective Metrics to Review

| Category | Metrics | Source |
|----------|---------|--------|
| Timeline | Planned vs. actual dates | Project tracker |
| Quality | Error rate, incidents, bugs | Monitoring |
| Adoption | Usage, activation, retention | Analytics |
| Business | Pipeline, revenue, wins | CRM |
| Sentiment | NPS, CSAT, social | Surveys, social |
| Effort | Estimated vs. actual hours | Time tracking |

### Institutional Knowledge Capture

```markdown
## Launch Playbook Update: Learnings from SSO Launch

### Added to Standard Checklist:
□ GDPR documentation (for EU-facing features)
□ Partner briefing (for integration features)
□ Setup video (for complex features)
□ CS playbook (for Tier 1-2 launches)

### Updated Standards:
- Enterprise feature beta: 6-8 weeks (was 4 weeks)
- Partner notification: T-2 weeks (was T-1 week)
- Competitive response plan: Required for Tier 1-2

### Templates Updated:
- Launch brief: Added competitive section
- Enablement checklist: Added video requirement
- Support prep: Expanded FAQ template
```

### Anti-Patterns

- **Skipping the retro** — "We're too busy with the next thing"
- **Blame game** — Focusing on who, not what
- **No metrics** — Opinions without data
- **Too soon** — Before results are measurable
- **Too late** — Details forgotten
- **No actions** — Insights without follow-through
- **Same mistakes** — Not consulting past retros
- **Missing stakeholders** — Only PM attends
- **Rushed timing** — Friday 5pm, everyone checked out
