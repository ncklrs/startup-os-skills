---
title: A/B Testing Framework
impact: HIGH
tags: ab-testing, experimentation, optimization, testing
---

## A/B Testing Framework

**Impact: HIGH**

A/B testing without a framework is just guessing with data. Structured testing compounds learnings over time.

### The Testing Hierarchy

Test in this order for maximum impact:

| Priority | Element | Typical Impact |
|----------|---------|----------------|
| 1 | **Offer** | 50-200% lift |
| 2 | **Headline/Hook** | 20-100% lift |
| 3 | **CTA** | 10-50% lift |
| 4 | **Social proof** | 5-30% lift |
| 5 | **Layout/Design** | 5-20% lift |
| 6 | **Colors/Fonts** | 1-10% lift |

### Statistical Significance

| Sample Size | Minimum Duration | Confidence |
|-------------|------------------|------------|
| <1,000 visitors | 2+ weeks | Low |
| 1,000-5,000 | 1-2 weeks | Medium |
| 5,000-20,000 | 5-7 days | Good |
| 20,000+ | 3-5 days | High |

### Minimum Detectable Effect (MDE)

| Baseline CVR | Need to Detect | Sample Size/Variation |
|--------------|----------------|----------------------|
| 2% | 20% relative lift | ~16,000 |
| 5% | 20% relative lift | ~6,200 |
| 10% | 20% relative lift | ~3,000 |
| 20% | 20% relative lift | ~1,400 |

### Test Hypothesis Template

```
We believe [change] will [improve metric] because [rationale].
We will know this is true when [metric] increases by [X%] with [confidence]%.
```

### Good Test Hypotheses

```
✓ "We believe adding customer logos above the fold will increase
   form submissions by 15% because social proof reduces uncertainty."

✓ "We believe changing the CTA from 'Learn More' to 'Start Free Trial'
   will increase clicks by 25% because it's more specific and actionable."

✓ "We believe reducing form fields from 5 to 3 will increase
   completions by 30% because it reduces friction."
```

### Bad Test Hypotheses

```
✗ "We want to test a new button color"
  → No expected outcome, no rationale

✗ "Let's see if this new design performs better"
  → Vague, unmeasurable

✗ "The CEO thinks we should try this"
  → Not data-informed, HiPPO decision
```

### Testing Checklist (Pre-Launch)

- [ ] Hypothesis documented
- [ ] Single variable being tested
- [ ] Sample size calculated
- [ ] Test duration planned
- [ ] Primary metric defined
- [ ] Tracking verified
- [ ] QA on all variations
- [ ] Mobile/desktop checked
- [ ] Audience split randomized

### Testing Checklist (During)

- [ ] Don't peek early (peeking inflates false positives)
- [ ] Monitor for technical issues only
- [ ] Don't stop at first significance
- [ ] Run for full business cycle (week minimum)
- [ ] Document any external factors

### Testing Checklist (Post)

- [ ] Statistical significance confirmed
- [ ] Segment results analyzed
- [ ] Learnings documented
- [ ] Winner implemented
- [ ] Next test planned

### Common Test Ideas

| Category | Tests |
|----------|-------|
| **Headlines** | Benefit vs feature, specific vs general, question vs statement |
| **CTAs** | Action verb, color, size, placement, copy |
| **Social proof** | Logos vs testimonials, numbers vs names |
| **Forms** | Field count, layout, labels, validation timing |
| **Images** | Product vs people, illustration vs photo |
| **Pricing** | Display format, anchoring, decoy options |
| **Copy** | Long vs short, formal vs casual, we vs you |

### Segment Analysis

Don't just look at overall results. Check:

| Segment | Why It Matters |
|---------|----------------|
| **Device** | Mobile vs desktop behavior differs |
| **Traffic source** | Paid vs organic intent differs |
| **New vs returning** | Familiarity changes behavior |
| **Geography** | Cultural differences |
| **Time of day** | Business hours vs evenings |

### False Positive Prevention

| Risk | Mitigation |
|------|------------|
| **Peeking** | Pre-commit to duration, use sequential testing |
| **Multiple comparisons** | Bonferroni correction, primary metric only |
| **Novelty effect** | Run tests longer, track over time |
| **Sample ratio mismatch** | Verify 50/50 split with chi-square |
| **Selection bias** | Randomize properly, check pre-period |

### Documentation Template

```
## Test: [Name]
**Date:** [Start] - [End]
**Hypothesis:** [Statement]
**Primary Metric:** [Metric]
**Sample Size:** [N per variation]

### Variations
- Control: [Description]
- Treatment: [Description]

### Results
| Variation | Visitors | Conversions | CVR | Lift |
|-----------|----------|-------------|-----|------|
| Control   |          |             |     | -    |
| Treatment |          |             |     |      |

**Statistical Significance:** [Yes/No, p-value]
**Confidence:** [%]

### Key Learnings
- [Learning 1]
- [Learning 2]

### Next Steps
- [Action item]
```

### Anti-Patterns

- **Testing too many things** — Can't isolate what caused change
- **Stopping early** — False positives from peeking
- **Running too long** — Novelty effect wears off
- **Ignoring segments** — Average hides important differences
- **No documentation** — Same mistakes repeated
- **Copying others' tests** — Context matters, test for your audience
- **HiPPO decisions** — Highest Paid Person's Opinion overrules data
- **Winner-take-all thinking** — Learn from losers too
