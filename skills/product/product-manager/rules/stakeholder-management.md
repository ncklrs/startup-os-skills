---
title: Stakeholder Management
impact: HIGH
tags: stakeholder, communication, alignment, influence
---

## Stakeholder Management

**Impact: HIGH**

PMs don't have authority — they have influence. Master the art of aligning diverse stakeholders around shared outcomes.

### Stakeholder Mapping Matrix

```
                    High Influence
                         │
         ┌───────────────┼───────────────┐
         │               │               │
         │    MANAGE     │   PARTNER     │
         │   CLOSELY     │   ACTIVELY    │
         │  (keep happy) │ (collaborate) │
         │               │               │
Low      │               │               │   High
Interest─┼───────────────┼───────────────┼───Interest
         │               │               │
         │    MONITOR    │   KEEP        │
         │   (minimal)   │   INFORMED    │
         │               │               │
         └───────────────┼───────────────┘
                         │
                    Low Influence
```

### Stakeholder Communication Guide

| Stakeholder | What They Care About | Communication Style | Cadence |
|-------------|---------------------|---------------------|---------|
| **CEO/Executives** | Revenue impact, strategy alignment | Outcomes, metrics, bottom line | Monthly + ad-hoc |
| **Engineering Lead** | Technical feasibility, team capacity | Detailed, collaborative | Daily |
| **Design Lead** | User experience, design quality | Visual, user-centric | Daily |
| **Sales** | Pipeline, competitive positioning | Customer stories, timelines | Weekly |
| **Marketing** | Positioning, launch timing | Messaging, dates | Weekly |
| **Customer Success** | User satisfaction, churn risk | Pain points, solutions | Weekly |
| **Finance** | ROI, resource allocation | Numbers, projections | Monthly |
| **Legal** | Compliance, risk | Specifics, documentation | As needed |

### Managing Up: Executive Communication

**Good Executive Update:**

```markdown
## Product Update - March 2024

### Headline
Activation rate improved 8% (23% → 31%), on track for Q1 target of 35%

### Key Wins
- Onboarding v2 shipped (March 1)
- Time-to-first-value reduced from 3 days to 1.5 days
- NPS improved 12 points for new users

### Risks & Blockers
- Mobile app delayed 4 weeks (replatforming decision)
  - Mitigation: Web experience prioritized
- Enterprise deal at risk due to SSO timeline
  - Mitigation: Fast-track SSO for Q2

### Next Month Focus
- Complete onboarding v2.1 (remaining 15% of flow)
- Launch template library (addresses top user request)
- Begin mobile app development

### Asks
- Decision needed: Expand engineering team by 2 in Q2?
- Awareness: Competitor X launched similar feature
```

**Bad Executive Update:**

```markdown
## Product Update

We shipped 47 features this month including dark mode,
new icons, dashboard improvements, and various bug fixes.
The team is working hard on the roadmap. We have some
delays but are managing them. Let me know if you have
any questions.
```

**Why this fails:**
- No connection to outcomes
- Feature counting vs. impact
- Vague on risks
- No asks or decisions needed

### Managing Across: Cross-Functional Alignment

**RACI for Feature Launch:**

| Activity | PM | Engineering | Design | Marketing | Sales |
|----------|:--:|:-----------:|:------:|:---------:|:-----:|
| Requirements | A | C | C | I | C |
| Technical spec | C | A | I | - | - |
| Design | C | C | A | I | - |
| Development | I | A | C | - | - |
| QA | I | A | C | - | - |
| Launch plan | A | I | I | R | C |
| Sales enablement | R | I | I | A | C |
| Customer comms | A | - | I | R | C |

**Legend:** R=Responsible, A=Accountable, C=Consulted, I=Informed

### Handling Conflicting Priorities

**Step 1: Acknowledge all perspectives**
```
"I understand Sales needs feature X for the enterprise deal,
and Engineering is concerned about technical debt. Both are
valid and important."
```

**Step 2: Reframe around shared goals**
```
"We all want sustainable revenue growth. Let's figure out
how to balance short-term wins with long-term health."
```

**Step 3: Use data to facilitate**
```
"Here's what the data tells us: Feature X impacts $200K deal,
technical debt is causing 20% velocity reduction. Let's discuss
the trade-off."
```

**Step 4: Make a recommendation**
```
"My recommendation: Ship a scoped version of Feature X in
2 weeks, then dedicate the next sprint to debt reduction."
```

### Saying No Gracefully

| Situation | Bad Response | Good Response |
|-----------|--------------|---------------|
| Feature request | "No, we can't do that" | "That's interesting. Help me understand the problem you're solving." |
| Timeline pressure | "That's impossible" | "Here's what we can deliver by then, and what requires more time." |
| Scope creep | "That's out of scope" | "Great idea. Let's add it to the backlog and prioritize it next planning." |
| Resource ask | "We don't have capacity" | "Here's our current commitments. What would you deprioritize to fit this?" |

### Building Trust Template

**Weekly stakeholder touchpoint agenda:**

```markdown
## 1:1 with [Stakeholder] - [Date]

### Open with listening (5 min)
- What's on your mind this week?
- Any concerns I should know about?

### Align on priorities (10 min)
- Here's where we are on [their interest]
- Here's what's coming next
- Any questions or concerns?

### Address blockers (10 min)
- Do you need anything from me?
- Here's what I need from you

### Close with commitment (5 min)
- Recap action items
- Confirm next touchpoint
```

### Influence Without Authority

**Techniques that work:**

| Technique | How to Apply |
|-----------|--------------|
| **Social proof** | "Engineering teams at Stripe do this..." |
| **Shared goals** | "We both want users to succeed..." |
| **Data evidence** | "The numbers show..." |
| **Small wins** | Start with easy asks, build credibility |
| **Find champions** | Identify allies, let them advocate |
| **Trade-offs** | "If we do X, we get Y" |

### Anti-Patterns

- **Avoidance** — Hoping conflicts resolve themselves
- **People pleasing** — Saying yes to everyone
- **Surprise attacks** — Springing decisions without warning
- **Email warfare** — Fighting battles over email
- **Going over heads** — Escalating before trying to resolve
- **Information hoarding** — Not sharing context freely
- **Blame games** — Pointing fingers when things fail
