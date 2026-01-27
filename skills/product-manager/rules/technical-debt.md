---
title: Technical Debt Management
impact: MEDIUM-HIGH
tags: technical-debt, engineering, maintenance, quality
---

## Technical Debt Management

**Impact: MEDIUM-HIGH**

Technical debt is the hidden tax on velocity. Great PMs understand, prioritize, and advocate for healthy codebases.

### What is Technical Debt?

```
┌─────────────────────────────────────────────────────────────────┐
│                    TECHNICAL DEBT TYPES                         │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│   DELIBERATE                          ACCIDENTAL                │
│   ───────────                         ──────────                │
│   "We know this is a shortcut,        "We didn't know better    │
│    we'll fix it later"                 at the time"             │
│                                                                 │
│   PRUDENT                             RECKLESS                  │
│   ───────                             ────────                  │
│   "Ship now, refactor later           "What's a design          │
│    with learnings"                     pattern?"                │
│                                                                 │
│   ┌─────────────────────────────────────────────────────────┐  │
│   │            DELIBERATE + PRUDENT = STRATEGIC             │  │
│   │           (Acceptable, plan for repayment)              │  │
│   └─────────────────────────────────────────────────────────┘  │
│                                                                 │
│   ┌─────────────────────────────────────────────────────────┐  │
│   │            RECKLESS + ACCIDENTAL = CRISIS               │  │
│   │             (Emergency, needs immediate fix)            │  │
│   └─────────────────────────────────────────────────────────┘  │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### Types of Technical Debt

| Type | Description | Impact | Example |
|------|-------------|--------|---------|
| **Code debt** | Poor code quality | Slower development | Spaghetti code, no tests |
| **Architecture debt** | Outdated design patterns | Hard to scale | Monolith needing microservices |
| **Dependency debt** | Outdated libraries | Security risk | jQuery 1.x, old Node version |
| **Documentation debt** | Missing/outdated docs | Onboarding friction | No API docs |
| **Test debt** | Insufficient test coverage | Bug risk | 30% coverage |
| **Infrastructure debt** | Legacy systems | Reliability issues | EOL databases |

### Technical Debt Prioritization Matrix

```
                    High Business Risk
                         │
         ┌───────────────┼───────────────┐
         │               │               │
         │   SCHEDULE    │   FIX NOW     │
         │   (plan it)   │   (urgent)    │
         │               │               │
Low      │               │               │   High
Effort───┼───────────────┼───────────────┼───Effort
         │               │               │
         │   ACCEPT      │   SCHEDULE    │
         │   (live with) │   (plan it)   │
         │               │               │
         └───────────────┼───────────────┘
                         │
                    Low Business Risk
```

### Debt Inventory Template

```markdown
## Technical Debt Inventory

### Critical (Address within 2 sprints)

| ID | Description | Impact | Effort | Owner |
|----|-------------|--------|--------|-------|
| TD-001 | Auth library 2 versions behind (CVE) | Security risk | 2 days | @alice |
| TD-002 | No rate limiting on public API | Stability risk | 3 days | @bob |

### High (Address this quarter)

| ID | Description | Impact | Effort | Owner |
|----|-------------|--------|--------|-------|
| TD-003 | Test coverage at 45% | Bug escape rate | 2 weeks | Team |
| TD-004 | Dashboard query N+1 problem | Performance | 1 week | @carol |

### Medium (Address this half)

| ID | Description | Impact | Effort | Owner |
|----|-------------|--------|--------|-------|
| TD-005 | Outdated monitoring setup | Incident response | 2 weeks | @dave |
| TD-006 | Documentation gaps | Onboarding time | 1 week | Team |

### Low (Backlog)

| ID | Description | Impact | Effort | Owner |
|----|-------------|--------|--------|-------|
| TD-007 | Legacy CSS framework | Dev velocity | 4 weeks | - |
| TD-008 | Inconsistent API responses | Developer experience | 2 weeks | - |
```

### Balancing Features and Debt

**Recommended Sprint Allocation:**

| Team Stage | Features | Bugs | Tech Debt |
|------------|----------|------|-----------|
| **Early (0-1)** | 80% | 15% | 5% |
| **Growth (1-2)** | 70% | 15% | 15% |
| **Scale (2+)** | 60% | 15% | 25% |
| **Debt crisis** | 40% | 10% | 50% |

### Communicating Debt to Leadership

**Good debt communication:**

```markdown
## Technical Debt Update - Q1 2024

### Summary
Current tech debt is impacting velocity by ~20%. Without
investment, we project 30% impact by Q3.

### Business Impact
| Debt Item | Current Impact | If Unaddressed |
|-----------|----------------|----------------|
| Test coverage (45%) | 2 bugs/week escape to prod | 4+ bugs/week |
| API performance | 3s load time (2x competitors) | Customer churn |
| Legacy auth | 1 day/sprint maintenance | Security incident |

### Recommended Investment
Allocate 20% of Q2 capacity (6 person-weeks) to:
1. Improve test coverage to 70% (2 weeks)
2. Optimize API queries (2 weeks)
3. Auth library upgrade (2 weeks)

### ROI Projection
- Bug escape rate: -50%
- Development velocity: +15%
- Security risk: Significantly reduced

### Decision Needed
Approve 20% debt allocation in Q2?
```

**Bad debt communication:**

```markdown
We have a lot of tech debt. The code is bad and we need to
rewrite it. Engineering is frustrated. Can we stop features
for a quarter?
```

**Why this fails:**
- No business impact framing
- No prioritization
- Vague ask
- No ROI case

### Making the Case for Debt Work

| Argument | Evidence |
|----------|----------|
| **Velocity impact** | "Features taking 2x longer due to workarounds" |
| **Bug rate** | "40% of bugs trace to legacy code" |
| **Security** | "CVE in dependency with no planned fix" |
| **Hiring/retention** | "Engineers cite codebase in exit interviews" |
| **Customer impact** | "Performance complaints up 50% YoY" |
| **Future cost** | "Fixing now: 2 weeks. Fixing later: 2 months" |

### Tech Debt Sprint Patterns

**Pattern 1: Percentage Allocation**
- Every sprint: 15-20% capacity for debt
- Pros: Consistent progress
- Cons: May not complete large items

**Pattern 2: Debt Sprints**
- Every 4th sprint: 100% debt focus
- Pros: Complete larger items
- Cons: Feature pause, coordination

**Pattern 3: Boy Scout Rule**
- "Leave code better than you found it"
- Pros: Continuous improvement
- Cons: Hard to track, may not address big items

**Pattern 4: Hack Weeks**
- Quarterly: Full week debt focus
- Pros: Team morale, big wins
- Cons: Infrequent, items pile up

### Preventing New Debt

| Practice | How It Helps |
|----------|--------------|
| **Code review** | Catches shortcuts before merge |
| **Definition of Done** | Include tests, docs, no known debt |
| **Architectural review** | Major changes get design review |
| **Debt tracking** | Visible backlog, not hidden |
| **Time for quality** | Don't force shortcuts via timelines |

### Tech Debt Retrospective Questions

1. What shortcuts did we take this quarter?
2. What's slowing us down the most?
3. What keeps breaking?
4. What would we do differently if starting fresh?
5. What are engineers most frustrated by?
6. What would make onboarding new developers easier?

### Anti-Patterns

- **Debt denial** — "We don't have tech debt"
- **Debt hoarding** — Tracking but never addressing
- **Big bang rewrites** — "Let's rewrite everything"
- **Invisible debt** — Not tracking or communicating
- **Feature tunnel vision** — Only new work, never maintenance
- **Gold plating** — Fixing debt that doesn't matter
- **Blaming engineers** — Debt is a business decision
- **No prioritization** — All debt is equal (it's not)
