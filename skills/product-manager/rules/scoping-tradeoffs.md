---
title: Feature Scoping and Trade-offs
impact: HIGH
tags: scoping, mvp, trade-offs, requirements, specs
---

## Feature Scoping and Trade-offs

**Impact: HIGH**

Great PMs ship value early and often. Master the art of scoping to deliver maximum impact with minimum effort.

### The MVP Mindset

```
                    VALUE DELIVERED
                         │
         ┌───────────────┼───────────────┐
         │               │               │
         │   Don't       │   MVP         │
         │   Build       │   (Start      │
         │   (waste)     │    here)      │
         │               │               │
Low      │               │               │   High
Learning─┼───────────────┼───────────────┼───Learning
         │               │               │
         │   Avoid       │   Eventually  │
         │   (risky)     │   (grow into) │
         │               │               │
         └───────────────┼───────────────┘
                         │
                    VALUE DELIVERED
```

### Scoping Levels

| Level | Definition | Timeline | Detail |
|-------|------------|----------|--------|
| **Skateboard** | Solves core problem, minimum features | 1-2 weeks | Validate hypothesis |
| **Scooter** | Core + most important enhancement | 2-4 weeks | Early adopter ready |
| **Bicycle** | Full MVP, ready for growth | 4-8 weeks | General availability |
| **Motorcycle** | Mature feature, optimized | Quarter+ | Scale and polish |
| **Car** | Full vision realized | Year+ | Enterprise-ready |

### Good Scoping Example: Notification System

```markdown
## Feature: Notification System

### Business Context
Users miss important updates, leading to 15% churn within 30 days.
Goal: Reduce "missed update" churn by 50%.

### Scoping Options

#### Skateboard (Week 1-2) — RECOMMENDED START
- Email notifications for critical events only
  - Failed payment
  - Approaching usage limit
  - Team invitation
- Single email template
- No preferences (always on)
- Success metric: Open rate > 40%

#### Scooter (Week 3-4)
- Add 5 more notification types
- Basic email preferences (all/none per category)
- In-app notification bell (unread count only)

#### Bicycle (Month 2)
- Full notification preferences by type/channel
- In-app notification center with history
- Push notifications (web)
- Real-time in-app badges

#### Motorcycle (Q3)
- Mobile push notifications
- Slack/Teams integration
- Notification digests (daily/weekly)
- Smart notification timing

### Recommendation
Start with Skateboard. We can validate email engagement
before building more complex infrastructure.
```

### Bad Scoping Example

```markdown
## Feature: Notification System

We need to build a full notification system with:
- Email, push, SMS, in-app, and Slack
- User preferences for every notification type
- Real-time delivery
- Notification history
- Analytics dashboard
- A/B testing for templates

Timeline: 2 months
```

**Why this fails:**
- All or nothing approach
- No prioritization
- No connection to outcomes
- High risk of delays

### Trade-off Framework: The Iron Triangle

```
                    ┌─────────┐
                    │  SCOPE  │
                    └────┬────┘
                         │
         ┌───────────────┼───────────────┐
         │               │               │
    ┌────┴────┐     ┌────┴────┐     ┌────┴────┐
    │   TIME  │─────│ QUALITY │─────│   COST  │
    └─────────┘     └─────────┘     └─────────┘

    Pick 2. The third flexes.
```

### Trade-off Communication Template

```markdown
## Trade-off Decision: Feature X

### Situation
We have 3 weeks until launch. Current estimate: 5 weeks.

### Options

#### Option A: Reduce scope (RECOMMENDED)
- Cut: Advanced filtering, bulk actions
- Keep: Core functionality, basic filtering
- Risk: Some power users disappointed
- Benefit: Ships on time, validates core value

#### Option B: Extend timeline
- Cut: Nothing
- Delay: 2 weeks
- Risk: Misses marketing campaign
- Benefit: Full feature set

#### Option C: Add resources
- Add: 2 contractors
- Risk: Onboarding time, coordination overhead
- Benefit: Might recover 1 week

### Recommendation
Option A. We can add cut features in v1.1 based on
user feedback. Launching on time is critical.

### Decision needed by: [Date]
```

### Scope Creep Defense

| Creep Type | Example | Defense |
|------------|---------|---------|
| **Edge case obsession** | "What if user has 10,000 items?" | "Let's validate core case first, optimize later" |
| **Gold plating** | "While we're there, add dark mode" | "Great idea! Added to backlog for v2" |
| **Stakeholder add-ons** | "Sales needs this one more thing" | "Help me understand the trade-off" |
| **Perfectionism** | "The animation isn't smooth enough" | "Ship it, iterate based on feedback" |
| **Future-proofing** | "We should build for 100x scale" | "Let's solve today's problem, we can scale later" |

### MoSCoW for Feature Scoping

```markdown
## Feature X Scope

### Must Have (v1.0 - 2 weeks)
- Core functionality that solves primary use case
- Basic error handling
- Mobile-responsive

### Should Have (v1.1 - +1 week)
- Secondary use case support
- Improved error messages
- Performance optimization

### Could Have (v1.2 - +2 weeks)
- Power user features
- Keyboard shortcuts
- Bulk operations

### Won't Have (Future consideration)
- API access
- White-labeling
- Enterprise features
```

### Questions to Reduce Scope

Ask these to find what can be cut:

1. **"What's the smallest thing that would be valuable?"**
2. **"If we had one week, what would we build?"**
3. **"What would users forgive being missing?"**
4. **"Can this be manual before automated?"**
5. **"Can we use existing infrastructure?"**
6. **"What can we learn before building?"**
7. **"Is this a must-have or nice-to-have?"**

### Scope Negotiation Phrases

| Instead of... | Say... |
|---------------|--------|
| "We can't do that" | "Here's what we can do in that timeframe" |
| "That's out of scope" | "Great idea — let's add it to v2 consideration" |
| "That's too much work" | "Let me show you the trade-offs" |
| "No" | "Yes, and here's what that would require" |

### Anti-Patterns

- **Big bang releases** — Building for months before shipping
- **Scope fear** — Afraid to cut anything
- **Spec-driven development** — Writing perfect specs for months
- **All or nothing** — "Either we do it right or not at all"
- **User-requested features** — Building exactly what users ask for (not their problem)
- **Premature optimization** — Building for scale before product-market fit
- **Ignoring constraints** — Pretending resources are unlimited
