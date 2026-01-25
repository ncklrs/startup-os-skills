---
title: Prioritization Frameworks
impact: CRITICAL
tags: prioritization, rice, ice, moscow, decision-making
---

## Prioritization Frameworks

**Impact: CRITICAL**

Prioritization is the PM's most important job. Use frameworks to make decisions transparent, defensible, and consistent.

### Framework Selection Guide

| Framework | Best For | Speed | Rigor | When to Use |
|-----------|----------|-------|-------|-------------|
| **RICE** | Feature prioritization | Medium | High | Quarterly planning |
| **ICE** | Quick comparisons | Fast | Medium | Weekly decisions |
| **MoSCoW** | Release scoping | Fast | Low | Sprint planning |
| **Kano** | Customer satisfaction | Slow | High | Annual strategy |
| **Value/Effort** | Visual prioritization | Fast | Low | Brainstorming |

### RICE Framework (Detailed)

```
RICE Score = (Reach × Impact × Confidence) / Effort
```

| Factor | Definition | Scale |
|--------|------------|-------|
| **Reach** | Users affected per quarter | Absolute number |
| **Impact** | Effect on goal per user | 3=massive, 2=high, 1=medium, 0.5=low, 0.25=minimal |
| **Confidence** | How sure are we? | 100%=high, 80%=medium, 50%=low |
| **Effort** | Person-months to build | Absolute number |

**RICE Example Calculation:**

| Feature | Reach | Impact | Confidence | Effort | Score |
|---------|-------|--------|------------|--------|-------|
| Onboarding redesign | 10,000 | 2 | 80% | 3 | 5,333 |
| Dark mode | 5,000 | 0.5 | 100% | 1 | 2,500 |
| API webhooks | 500 | 3 | 80% | 2 | 600 |
| SSO | 200 | 2 | 100% | 4 | 100 |

**Winner:** Onboarding redesign (highest RICE score)

### ICE Framework (Quick Scoring)

```
ICE Score = Impact × Confidence × Ease
```

All factors scored 1-10:
- **Impact:** How much will this move the needle?
- **Confidence:** How sure are we about impact and effort?
- **Ease:** How easy is this to implement?

**ICE Example:**

| Feature | Impact | Confidence | Ease | Score |
|---------|--------|------------|------|-------|
| Email optimization | 7 | 9 | 8 | 504 |
| New pricing page | 8 | 6 | 7 | 336 |
| Feature X | 6 | 5 | 9 | 270 |

### MoSCoW for Release Scoping

| Category | Definition | Decision Rule |
|----------|------------|---------------|
| **Must Have** | Release fails without it | Non-negotiable |
| **Should Have** | Important but not critical | Include if possible |
| **Could Have** | Nice to have | Include with extra capacity |
| **Won't Have** | Explicitly out of scope | Defer to future |

**Good MoSCoW Example:**

```markdown
## v2.3 Release Scope

### Must Have (Ship or don't release)
- [ ] Fix critical payment bug (#1234)
- [ ] GDPR delete endpoint compliance
- [ ] Performance fix for dashboard load

### Should Have (Plan for these)
- [ ] Improved error messages
- [ ] Bulk export feature
- [ ] Email notification preferences

### Could Have (Stretch goals)
- [ ] Dark mode toggle
- [ ] Keyboard shortcuts
- [ ] Widget redesign

### Won't Have (Explicitly deferred)
- Mobile app improvements (v2.4)
- API v2 (Q3 initiative)
- Multi-language support (2025)
```

### Value vs Effort Matrix

```
                    High Value
                         │
         ┌───────────────┼───────────────┐
         │               │               │
         │   STRATEGIC   │  QUICK WINS   │
         │   (plan for)  │  (do first)   │
         │               │               │
High     │               │               │   Low
Effort───┼───────────────┼───────────────┼───Effort
         │               │               │
         │   MONEY PIT   │   FILL-INS    │
         │  (avoid)      │  (do if time) │
         │               │               │
         └───────────────┼───────────────┘
                         │
                    Low Value
```

**Quadrant Actions:**
- **Quick Wins:** Do immediately, low effort + high value
- **Strategic:** Plan carefully, worth the investment
- **Fill-ins:** Good for new team members or slack time
- **Money Pit:** Explicitly say no

### Kano Model

| Type | User Expectation | If Present | If Absent |
|------|------------------|------------|-----------|
| **Basic** | Expected | Neutral | Dissatisfied |
| **Performance** | Wanted | Satisfied | Dissatisfied |
| **Delighters** | Unexpected | Delighted | Neutral |

**Example by Category:**

- **Basic:** App doesn't crash, data is saved
- **Performance:** Faster load times, more storage
- **Delighter:** AI suggestions, proactive insights

### Prioritization Meeting Template

```markdown
## Prioritization Review - [Date]

### Inputs
- Current backlog: [X items]
- Engineering capacity: [Y story points]
- Strategic goals: [List 2-3]

### Scoring Results
| Rank | Item | RICE Score | Owner Notes |
|------|------|------------|-------------|
| 1 | Feature A | 5,333 | Aligned to activation goal |
| 2 | Feature B | 2,500 | Customer request volume |
| 3 | Feature C | 600 | Strategic bet |

### Decisions
- Prioritized: [Items moving forward]
- Deprioritized: [Items deferred]
- Needs research: [Items needing discovery]

### Next Steps
- [ ] Update roadmap
- [ ] Communicate to stakeholders
- [ ] Begin spec work on top items
```

### Anti-Patterns

- **HiPPO** — Highest Paid Person's Opinion overrides data
- **Squeaky wheel** — Loudest stakeholder wins
- **FIFO** — First request in, first built
- **Framework worship** — Blindly following scores without judgment
- **No framework** — Pure gut feel without transparency
- **Gaming scores** — Inflating numbers to justify decisions already made
- **Analysis paralysis** — Scoring everything, deciding nothing
