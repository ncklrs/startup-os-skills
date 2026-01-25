---
title: Experimentation Design and Process
impact: HIGH
tags: experiment, design, hypothesis, process
---

## Experimentation Design and Process

**Impact: HIGH**

Beyond A/B testing mechanics lies experiment design: asking the right questions, designing valid tests, and building a culture of learning.

### The Experimentation Hierarchy

```
Level 5: Continuous Experimentation  ← Org-wide, embedded culture
            │
Level 4: Experiment Platform         ← Self-serve, scaled testing
            │
Level 3: Regular A/B Testing         ← Team runs experiments routinely
            │
Level 2: Ad-hoc Experiments          ← Occasional, project-based
            │
Level 1: No Experiments              ← Ship and hope
```

### Experiment Prioritization

**ICE Framework:**

| Factor | Question | Score (1-10) |
|--------|----------|--------------|
| **Impact** | How much lift if it wins? | Estimated % improvement |
| **Confidence** | How likely to win? | Evidence strength |
| **Ease** | How hard to implement? | Inverse of effort |

**ICE Score = Impact × Confidence × Ease**

**Prioritization Example:**

```
Experiment Ideas Ranked:
┌────────────────────────────────────────────────────────────┐
│ Idea                      │ I │ C │ E │ Score │ Priority  │
├────────────────────────────────────────────────────────────┤
│ Simplify signup form      │ 8 │ 7 │ 8 │  448  │ 1st       │
│ Add social proof          │ 6 │ 8 │ 9 │  432  │ 2nd       │
│ Redesign onboarding       │ 9 │ 5 │ 4 │  180  │ 3rd       │
│ New pricing page          │ 7 │ 4 │ 3 │   84  │ 4th       │
└────────────────────────────────────────────────────────────┘
```

### Hypothesis Development

**From Observation to Hypothesis:**

```
1. Observation
   "Users are dropping off after signup"

2. Research
   - Funnel data: 45% drop between signup and first action
   - Session recordings: Users seem confused by dashboard
   - Survey: "I didn't know what to do first"

3. Insight
   "Users lack clear guidance to their first valuable action"

4. Hypothesis
   "Adding a guided first-action wizard will increase
   signup-to-first-action rate by 15% because users
   will have clear direction"

5. Experiment Design
   - Control: Current post-signup experience
   - Treatment: Guided wizard to first action
   - Primary metric: First action completion (7 days)
   - Sample: 5,000 per variant
```

### Types of Experiments

| Type | Description | When to Use |
|------|-------------|-------------|
| **A/B Test** | Control vs one variant | Optimization, validation |
| **A/B/n Test** | Control vs multiple variants | Exploring options |
| **Multivariate** | Multiple variables at once | UI optimization |
| **Holdout** | Exclude % from all changes | Measure cumulative impact |
| **Geo Experiment** | Different regions | When randomization hard |
| **Switchback** | Alternating on/off | Time-sensitive effects |
| **Bandit** | Adaptive allocation | Fast optimization |

### Experiment Documentation

**Experiment Brief Template:**

```
┌────────────────────────────────────────────────────────────┐
│                    EXPERIMENT BRIEF                        │
├────────────────────────────────────────────────────────────┤
│ Name: Guided Onboarding Wizard                             │
│ Owner: Sarah (PM), Jake (Eng)                              │
│ Status: Design Review                                      │
│ Start Date: TBD                                            │
├────────────────────────────────────────────────────────────┤
│ CONTEXT                                                    │
│ Current signup-to-first-action rate is 55%. User research  │
│ shows confusion about next steps. Competitors show 70%+.   │
├────────────────────────────────────────────────────────────┤
│ HYPOTHESIS                                                 │
│ Adding a 3-step guided wizard after signup will increase   │
│ first-action completion by 15% by providing clear          │
│ direction and reducing cognitive load.                     │
├────────────────────────────────────────────────────────────┤
│ VARIANTS                                                   │
│ Control (50%): Current experience (dashboard with tips)    │
│ Treatment (50%): Guided 3-step wizard                      │
├────────────────────────────────────────────────────────────┤
│ METRICS                                                    │
│ Primary: First action completion (7 days)                  │
│ Secondary: Time to first action, D7 retention              │
│ Guardrails: Skip rate, support tickets, D30 retention      │
├────────────────────────────────────────────────────────────┤
│ TARGETING                                                  │
│ Who: New signups only                                      │
│ Exclusions: Enterprise users, mobile app                   │
│ Sample size: 10,000 total (5,000/variant)                  │
│ Duration: 3 weeks minimum                                  │
├────────────────────────────────────────────────────────────┤
│ SUCCESS CRITERIA                                           │
│ Ship if: >10% lift with p<0.05, guardrails pass            │
│ Iterate if: 5-10% lift or mixed signals                    │
│ Kill if: <5% lift or guardrail regression                  │
├────────────────────────────────────────────────────────────┤
│ RISKS & MITIGATIONS                                        │
│ Risk: Wizard feels forced                                  │
│ Mitigation: Clear skip option, track skip rate             │
└────────────────────────────────────────────────────────────┘
```

### Good vs Bad Experiment Design

**Good: Complete, Rigorous, Learnable**

```
Experiment: Reduce Checkout Friction

Background:
- Cart abandonment at 68%
- Heatmaps show hesitation at shipping step
- Competitor analysis shows simpler flows

Hypothesis:
Combining shipping and billing into one step will increase
checkout completion by 12% by reducing perceived effort.

Design:
- A/B test, 50/50 split
- Primary: Checkout completion rate
- Secondary: Time to complete, support contacts
- Guardrails: Failed payments, address errors
- n = 8,000/variant (16,000 total)
- Duration: 4 weeks
- Segments: New vs returning, mobile vs desktop

Decision rules:
- >8% lift + p<0.05 + guardrails pass → Ship
- 3-8% lift → Extend + investigate segments
- <3% lift → Kill, learn, iterate

What we'll learn either way:
- Win: Friction reduction works, look for more
- Lose: Friction isn't the issue, test value prop
```

**Bad: Incomplete, No Learning**

```
Experiment: New Checkout

Test the new checkout page.

Variants:
- Old checkout
- New checkout

Run for 2 weeks.

Problems:
- No hypothesis
- No primary metric
- No sample size calculation
- No guardrails
- No decision criteria
- No learning documented
```

### Running an Experimentation Program

**Monthly Experiment Cadence:**

| Week | Activities |
|------|------------|
| **Week 1** | Analyze previous experiments, update backlog |
| **Week 2** | Design next experiments, build variants |
| **Week 3** | Launch experiments, monitor ramp |
| **Week 4** | Analyze results, document learnings |

**Experiment Pipeline:**

```
┌──────────────┐    ┌──────────────┐    ┌──────────────┐
│   BACKLOG    │ →  │   DESIGN     │ →  │  IMPLEMENT   │
│  (20+ ideas) │    │ (3-5 briefs) │    │  (2-3 ready) │
└──────────────┘    └──────────────┘    └──────────────┘
        │                   │                  │
        ▼                   ▼                  ▼
┌──────────────┐    ┌──────────────┐    ┌──────────────┐
│   RUNNING    │ ←  │   LAUNCHED   │ ←  │     QA       │
│  (2-4 live)  │    │  (ramping)   │    │  (testing)   │
└──────────────┘    └──────────────┘    └──────────────┘
        │
        ▼
┌──────────────┐    ┌──────────────┐
│   ANALYZE    │ →  │  DOCUMENT    │
│  (results)   │    │  (learnings) │
└──────────────┘    └──────────────┘
```

### Experiment Velocity Metrics

| Metric | Definition | Target |
|--------|------------|--------|
| **Experiments/Month** | Tests completed | 8-12 |
| **Win Rate** | % with positive result | 30-40% |
| **Coverage** | % of features tested | >40% |
| **Cycle Time** | Idea to result (days) | <21 |
| **Learning Rate** | Insights documented | 100% |

### Building Experiment Culture

**Signs of Good Culture:**

```
✓ PMs write hypotheses before building
✓ Engineers suggest experiments proactively
✓ Failed experiments are celebrated for learning
✓ Decisions cite experiment results
✓ Experiment results are shared widely
✓ Backlog is always full of ideas
```

**Signs of Poor Culture:**

```
✗ Experiments are done to "validate" decisions already made
✗ Inconclusive results are spun as wins
✗ Only "safe" experiments are run
✗ Results aren't documented or shared
✗ Leadership overrides experiment results
✗ Teams don't know experiment status
```

### Experimentation Ethics

| Principle | Guidelines |
|-----------|------------|
| **Informed users** | Disclose testing in terms of service |
| **No harm** | Don't test things that hurt users |
| **Fair value** | Don't withhold core value from control |
| **Privacy** | Only collect necessary data |
| **Sensitive topics** | Extra care with health, finance |

### Anti-Patterns

- **HIPPO culture** — Highest-paid person overrides data
- **P-hacking** — Running until you get significance
- **Cherry-picking** — Only reporting favorable segments
- **Feature factory** — Shipping without measuring
- **One-and-done** — Not iterating on learnings
- **Analysis paralysis** — Perfect is enemy of good
- **Cargo cult** — Running experiments without understanding stats
- **Winner's curse** — Expecting production results = test results
