---
title: A/B Testing and Experimentation
impact: HIGH
tags: experiment, ab-testing, hypothesis, statistics
---

## A/B Testing and Experimentation

**Impact: HIGH**

A/B testing removes opinion from product decisions. Done right, it's the difference between "we think" and "we know."

### When to A/B Test

| Scenario | A/B Test? | Why |
|----------|-----------|-----|
| **Optimizing existing flow** | Yes | Measure impact of changes |
| **Major redesign** | Maybe | Consider qualitative first |
| **New feature launch** | Yes | Validate before full rollout |
| **Copy/CTA changes** | Yes | Quick wins, clear measurement |
| **Pricing changes** | Carefully | Revenue impact, user trust |
| **Bug fixes** | No | Just fix it |
| **Low traffic areas** | No | Won't reach significance |

### Anatomy of a Good Experiment

```
┌────────────────────────────────────────────────────────────┐
│                    EXPERIMENT DESIGN                       │
├────────────────────────────────────────────────────────────┤
│ Hypothesis:                                                │
│   Changing the CTA from "Start Free" to "Start in 60      │
│   seconds" will increase signup rate by 10%                │
│                                                            │
│ Primary Metric: Signup completion rate                     │
│ Secondary Metrics: Time to signup, D7 retention            │
│ Guardrail Metrics: Page load time, error rate              │
│                                                            │
│ Sample Size: 5,000 per variant (10,000 total)              │
│ Duration: 14 days minimum                                  │
│ Significance Level (α): 5%                                 │
│ Power (1-β): 80%                                           │
│ MDE: 10% relative improvement                              │
│                                                            │
│ Variants:                                                  │
│   Control (50%): "Start Free"                              │
│   Treatment (50%): "Start in 60 seconds"                   │
│                                                            │
│ Segments to analyze: New vs returning, mobile vs desktop   │
│ Exclusions: Existing users, bot traffic                    │
└────────────────────────────────────────────────────────────┘
```

### The Hypothesis Formula

**Structure:**

```
If we [change X],
then [metric Y] will [increase/decrease] by [Z%],
because [reason/evidence].
```

**Good Example:**
```
If we reduce signup form fields from 6 to 3,
then signup completion rate will increase by 15%,
because user research showed field fatigue is the #1 drop-off reason.
```

**Bad Example:**
```
If we change the button color,
it might help,
because blue is nice.
```

### Sample Size and Duration

**Sample Size Calculation:**

| Baseline Rate | MDE | Required Sample/Variant |
|--------------|-----|------------------------|
| 1% | 10% relative (1.1%) | 150,000 |
| 5% | 10% relative (5.5%) | 30,000 |
| 10% | 10% relative (11%) | 15,000 |
| 20% | 10% relative (22%) | 6,500 |
| 50% | 10% relative (55%) | 1,600 |

**Duration Guidelines:**
```
Minimum: 1 full week (capture weekly patterns)
Typical: 2-4 weeks
Maximum before concern: 6-8 weeks

Factors extending duration:
- Low traffic volume
- Smaller expected effect
- Higher baseline variance
- Need for segment analysis
```

### Statistical Rigor

**Key Concepts:**

| Concept | Definition | Target |
|---------|------------|--------|
| **Significance (α)** | False positive rate | 5% (p < 0.05) |
| **Power (1-β)** | True positive rate | 80% |
| **MDE** | Minimum Detectable Effect | Smallest meaningful change |
| **Confidence Interval** | Range of true effect | Doesn't cross zero |

**Reading Results:**

```
Experiment Results:
┌─────────────────────────────────────────────────────────┐
│ Metric: Signup Completion Rate                          │
├─────────────────────────────────────────────────────────┤
│ Control:     12.4% (n=5,200)                            │
│ Treatment:   13.8% (n=5,180)                            │
│                                                         │
│ Relative Lift: +11.3%                                   │
│ Absolute Lift: +1.4 percentage points                   │
│ 95% CI: [+5.2%, +17.8%]                                 │
│ p-value: 0.002                                          │
│ Status: SIGNIFICANT                                     │
└─────────────────────────────────────────────────────────┘

Interpretation:
- Treatment wins with 11.3% improvement
- CI doesn't include zero = statistically significant
- p < 0.05 = reject null hypothesis
- Ready to ship treatment
```

### Common Testing Mistakes

| Mistake | Problem | Prevention |
|---------|---------|------------|
| **Peeking** | Stopping early on exciting results | Pre-set duration, sequential analysis |
| **P-hacking** | Running until significant | Pre-register hypothesis |
| **HARKing** | Hypothesizing after results | Document hypothesis before |
| **Segment hunting** | Finding any winning segment | Pre-define segments |
| **Ignoring power** | Too small sample | Calculate sample size upfront |
| **No guardrails** | Winning metric, losing elsewhere | Define counter-metrics |
| **Too many variants** | Diluted sample | Limit to 2-4 variants |

### Guardrail Metrics

```
Primary: Signup completion rate (trying to improve)

Guardrails (must not degrade):
┌─────────────────────────────────────────────────────────┐
│ Guardrail           │ Threshold    │ Result            │
├─────────────────────────────────────────────────────────┤
│ D7 retention        │ -5% max      │ -2% ✓             │
│ Page load time      │ +200ms max   │ +50ms ✓           │
│ Error rate          │ +0.5% max    │ +0.1% ✓           │
│ Support tickets     │ +10% max     │ -5% ✓             │
└─────────────────────────────────────────────────────────┘

Status: All guardrails passed, safe to ship
```

### Good vs Bad Experiment Design

**Good: Complete, Rigorous**
```
Experiment: Onboarding Flow Simplification

Background:
Current onboarding has 8 steps, 45% completion rate.
User research shows steps 4-6 cause most drop-offs.

Hypothesis:
Reducing onboarding from 8 to 5 steps (removing low-value steps)
will increase completion rate by 15% because users experience
less friction and see value faster.

Design:
- Primary metric: Onboarding completion rate
- Secondary: Time to complete, D7 activation
- Guardrails: Setup quality score, D30 retention
- Sample: 10,000/variant
- Duration: 3 weeks
- Targeting: New users only, all platforms

Success Criteria:
- Primary: >10% relative lift, p<0.05
- Guardrails: No degradation beyond thresholds
- Qualitative: User feedback positive

Decision Framework:
- If significant win: Ship to 100%
- If neutral: Consider qualitative findings
- If negative: Abandon, iterate
```

**Bad: Incomplete, Unmeasurable**
```
Experiment: Try New Onboarding

Let's test a new onboarding flow.

Variants: A (current) vs B (new)

Run for a week and see what happens.

Problems:
- No hypothesis
- No sample size calculation
- Arbitrary duration
- No guardrails
- No success criteria
- No decision framework
```

### Sequential Testing

For faster decisions with statistical validity:

```
Sequential Analysis Framework:
┌──────────────────────────────────────────────────────────┐
│ Check Point │ Cumulative n │ Continue if │ Stop if      │
├──────────────────────────────────────────────────────────┤
│ Day 3       │ 2,000        │ |z| < 2.8   │ |z| > 2.8    │
│ Day 7       │ 5,000        │ |z| < 2.5   │ |z| > 2.5    │
│ Day 14      │ 10,000       │ |z| < 2.2   │ |z| > 2.2    │
│ Day 21      │ 15,000       │ Final decision              │
└──────────────────────────────────────────────────────────┘

Benefits:
- Can stop early for clear winners/losers
- Maintains statistical validity
- Faster iteration cycle
```

### Experiment Velocity

| Metric | Target | Current |
|--------|--------|---------|
| **Experiments/month** | 8-12 | 6 |
| **Win rate** | 30-40% | 35% |
| **Time to decision** | 2 weeks | 3 weeks |
| **Experiment coverage** | 40% of features | 25% |

**Increasing Velocity:**
- Pre-built experiment templates
- Self-serve experiment platform
- Reduced approval friction
- Parallel testing where possible

### Anti-Patterns

- **HiPPO override** — Ignoring data for opinion
- **Winner's curse** — Effect sizes shrink in production
- **Novelty effects** — Early lift fades over time
- **Feature flag debt** — Experiments live forever
- **Analysis paralysis** — Running tests that don't matter
- **Underpowered tests** — Results too noisy to trust
- **One-and-done** — Not iterating on insights
- **No documentation** — Learnings lost to time
