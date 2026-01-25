---
title: Survey Design
impact: HIGH
tags: research, surveys, quantitative, validation
---

## Survey Design

**Impact: HIGH**

Surveys quantify what interviews discover. Use them to measure prevalence and priority, not to explore unknowns.

### When to Use Surveys

**Good Use Cases**
```
- Validate problem prevalence ("How many have this issue?")
- Prioritize features ("Which matters most?")
- Measure satisfaction (NPS, CSAT)
- Segment users by behavior
- Track changes over time
```

**Bad Use Cases**
```
- Discover new problems (use interviews)
- Understand "why" (surveys give what, not why)
- Predict future behavior (unreliable)
- Test new concepts (use prototype testing)
```

### Survey Design Principles

**1. Start with Objectives**
```
Before writing questions:
- What decision will this inform?
- What will you do differently based on results?
- How will you analyze the data?

Bad: "Let's see what people think about our product."
Good: "We need to decide which of 3 features to build first."
```

**2. Keep It Short**
```
Survey Length Impact:
- < 5 min: 80%+ completion
- 5-10 min: 60-70% completion
- 10-15 min: 40-50% completion
- > 15 min: < 30% completion

Rule: If you can cut a question, cut it.
```

**3. One Concept Per Question**
```
Bad: "Is our product easy to use and affordable?"
(What if it's easy but expensive?)

Good:
"How easy is our product to use?"
"How affordable is our product?"
```

### Question Types

| Type | When to Use | Example |
|------|-------------|---------|
| **Multiple choice** | Categorical data | "What's your role?" |
| **Rating scale** | Measure intensity | "How satisfied are you? 1-5" |
| **Likert scale** | Agreement/frequency | "Strongly disagree → Strongly agree" |
| **Ranking** | Prioritization | "Rank these features 1-5" |
| **Open-ended** | Qualitative depth | "What's your biggest challenge?" |
| **Matrix** | Multiple items, same scale | "Rate each feature: 1-5" |

### Writing Good Questions

**Good Questions**
```
Specific and measurable:
"In the past 30 days, how many times did you [action]?"

Clear options:
"Never / 1-2 times / 3-5 times / 6+ times"

Neutral wording:
"How would you rate X?"

Behavioral focus:
"When did you last [do X]?"
```

**Bad Questions**
```
Double-barreled:
"Is our product fast and reliable?"

Leading:
"How much do you love our new feature?"

Vague:
"Do you sometimes have problems?"

Hypothetical:
"Would you use a feature that does X?"

Jargon-heavy:
"How do you feel about our ML-powered NLP capabilities?"
```

### Scale Design

**Likert Scales (Agreement)**
```
5-point: Strongly disagree → Strongly agree
7-point: Same, with "Somewhat" options

Best practice:
- Use odd numbers for neutral midpoint
- Use even numbers to force a direction
- Be consistent throughout survey
```

**Rating Scales (Satisfaction/Quality)**
```
1-5: Simple, familiar, sufficient for most cases
1-7: More granularity when needed
1-10: Familiar but inconsistent interpretation

Best practice:
- Always label endpoints
- Consider labeling all points
- 1-5 is usually enough
```

**NPS (Net Promoter Score)**
```
"How likely are you to recommend X to a colleague?"
0-10 scale

Scoring:
- Promoters: 9-10
- Passives: 7-8
- Detractors: 0-6
- NPS = % Promoters - % Detractors

Always follow with: "What's the primary reason for your score?"
```

### Survey Structure

**Optimal Flow**
```
1. Screening questions (filter unqualified respondents)
2. Easy, engaging questions (build momentum)
3. Core questions (get key data)
4. Sensitive/demographic questions (save for end)
5. Open-ended questions (optional, for depth)
```

**Example Structure**
```
1. Screener: "Do you use [product category]?" (Yes/No)
2. Warmup: "What's your primary role?" (Multiple choice)
3. Core: "How satisfied are you with [X]?" (Scale)
4. Core: "Rank these features by importance" (Ranking)
5. Demographics: "Company size?" (Multiple choice)
6. Open: "What's missing from current solutions?" (Text)
```

### Sample Size Calculator

| Population | 95% Confidence, 5% Margin | 95% Confidence, 3% Margin |
|------------|---------------------------|---------------------------|
| 100 | 80 | 92 |
| 500 | 217 | 341 |
| 1,000 | 278 | 516 |
| 10,000 | 370 | 964 |
| 100,000+ | 384 | 1,067 |

**Quick Rule:**
- Small decisions: 50-100 responses
- Medium decisions: 100-300 responses
- Major decisions: 300+ responses

### Survey Distribution

| Channel | Response Rate | Bias | Best For |
|---------|---------------|------|----------|
| **In-app** | 10-30% | Active users | Product feedback |
| **Email** | 5-15% | Engaged users | Customer research |
| **Panel** | Varies | Can target | Market research |
| **Social** | 1-5% | Self-selected | Quick pulse checks |

**Increasing Response Rates**
```
- Keep it short (< 5 min)
- Explain why and who benefits
- Personalize invitation
- Offer incentive (carefully)
- Send reminders (2-3 max)
- Mobile-friendly design
```

### Analysis Framework

**Quantitative Analysis**
```
1. Response rate and completion rate
2. Descriptive stats (mean, median, distribution)
3. Segment comparisons (by role, company size, etc.)
4. Cross-tabulation (how does X relate to Y?)
5. Statistical significance (for major decisions)
```

**Open-Ended Analysis**
```
1. Read all responses
2. Code themes (tag with categories)
3. Count theme frequency
4. Pull representative quotes
5. Look for surprises
```

### Survey Template: Feature Prioritization

```
1. "What's your primary role?"
   [ ] Engineering [ ] Product [ ] Design [ ] Other

2. "How often do you [use case]?"
   [ ] Daily [ ] Weekly [ ] Monthly [ ] Rarely [ ] Never

3. "How important are each of these capabilities to you?"
   [1-5 scale for each feature]

4. "How satisfied are you with your current solution for each?"
   [1-5 scale for each feature]

5. "If you could only improve one thing, what would it be?"
   [Open text]

6. "Anything else we should know?"
   [Open text]
```

### Anti-Patterns

- **Survey-first research** — Surveying before interviewing (you'll ask wrong questions)
- **Too many questions** — Every question costs completions
- **Leading scales** — "Poor, Fair, Good, Great, Excellent" (biased toward positive)
- **Required open-ends** — People will write garbage to proceed
- **Survey fatigue** — Surveying same users too often
- **Ignoring completion rate** — 20% completion means 80% bias
- **Over-engineering** — Simple surveys beat complex ones
