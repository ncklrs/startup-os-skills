---
title: Roadmap Creation and Maintenance
impact: CRITICAL
tags: roadmap, strategy, planning, alignment
---

## Roadmap Creation and Maintenance

**Impact: CRITICAL**

A roadmap is a communication tool, not a promise. It aligns stakeholders around strategic direction while maintaining flexibility for learning.

### Roadmap Types by Audience

| Type | Audience | Horizon | Update Cadence | Format |
|------|----------|---------|----------------|--------|
| **Vision** | Board, investors | 2-5 years | Annually | Narrative + themes |
| **Strategic** | Leadership team | 12 months | Quarterly | Outcome-based |
| **Release** | Cross-functional | Quarter | Monthly | Feature-level |
| **Sprint** | Engineering team | 2 weeks | Per sprint | Story-level |

### The Now-Next-Later Framework

```
┌─────────────────────────────────────────────────────────────────┐
│                                                                 │
│   NOW              NEXT              LATER                      │
│   (Committed)      (Planned)         (Exploratory)              │
│                                                                 │
│   ┌──────────┐     ┌──────────┐     ┌──────────┐               │
│   │ Feature A│     │ Feature D│     │ Feature G│               │
│   │ Feature B│     │ Feature E│     │ Feature H│               │
│   │ Feature C│     │ Feature F│     │ Theme X  │               │
│   └──────────┘     └──────────┘     └──────────┘               │
│                                                                 │
│   High certainty   Medium certainty  Low certainty              │
│   Detailed specs   General scope     Problem-level              │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### Good Roadmap: Outcome-Based

```markdown
## Q1 2024 Roadmap

### Objective: Increase activation rate from 23% to 35%

**Now (January)**
- Onboarding flow redesign (addresses 40% drop-off at step 3)
- In-app guidance for first workflow creation
- Email sequence optimization for day 1-7

**Next (February-March)**
- Template library expansion (top request from churned users)
- Mobile app MVP (30% of signups are mobile-first)
- Integration with top 3 requested tools

**Later (Q2 consideration)**
- AI-powered setup assistant
- Team onboarding flow
- Advanced personalization

### Success Metrics
- Primary: Activation rate (23% → 35%)
- Secondary: Time-to-first-value (3 days → 1 day)
- Guardrail: Support ticket volume (maintain < 5% increase)
```

### Bad Roadmap: Feature Shopping List

```markdown
## Q1 2024 Roadmap

### January
- Dark mode
- Export to CSV
- User avatars
- Password reset improvements

### February
- Dashboard redesign
- New chart types
- API v2
- Mobile app

### March
- SSO integration
- Webhooks
- Custom domains
- White labeling
```

**Why this fails:**
- No strategic context or "why"
- No connection to outcomes
- Encourages date-based commitments
- No prioritization rationale

### Roadmap Maintenance Rhythm

| Activity | Frequency | Participants |
|----------|-----------|--------------|
| Vision review | Annually | Leadership + Board |
| Strategic alignment | Quarterly | Product + Leadership |
| Roadmap review | Monthly | Product + Stakeholders |
| Prioritization | Bi-weekly | Product Trio |
| Backlog grooming | Weekly | PM + Engineering |

### Communicating Roadmap Changes

**When priorities shift:**

```markdown
## Roadmap Update: March 2024

### What Changed
Mobile app MVP moved from Q1 → Q2

### Why
- User research revealed web activation is the primary bottleneck
- Mobile users who activate on web have 2x retention
- Engineering capacity needed for onboarding improvements

### Impact
- Users requesting mobile: Delayed by ~6 weeks
- Onboarding improvements: Accelerated by 4 weeks
- Expected activation lift: +8% (vs +3% from mobile)

### Next Review
April roadmap review will reassess mobile timeline
```

### Roadmap Review Questions

Before finalizing any roadmap:

1. **Strategic alignment** — Does this ladder up to company goals?
2. **Customer value** — What problems does this solve?
3. **Measurable outcomes** — How will we know it worked?
4. **Dependencies** — What must happen first?
5. **Risks** — What could prevent success?
6. **Trade-offs** — What are we NOT doing?

### Anti-Patterns

- **Date-driven** — "We promised this for March" over strategic fit
- **Feature-centric** — Lists of features without outcomes
- **Stakeholder appeasement** — Something for everyone, focus for no one
- **Set and forget** — Creating once, never updating
- **Overly detailed futures** — Specifying Q4 at the same level as Q1
- **No flexibility** — Treating roadmap as contract, not hypothesis
