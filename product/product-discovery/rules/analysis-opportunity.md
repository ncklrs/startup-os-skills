---
title: Opportunity Sizing & Prioritization
impact: HIGH
tags: analysis, opportunity, prioritization, roadmap
---

## Opportunity Sizing & Prioritization

**Impact: HIGH**

Not all opportunities are equal. Sizing and prioritization ensure you work on problems worth solving for markets worth serving.

### Market Sizing Fundamentals

**TAM, SAM, SOM**

```
┌─────────────────────────────────────────────────────────┐
│                         TAM                             │
│         Total Addressable Market                        │
│    "Everyone who could possibly buy"                    │
│                                                         │
│    ┌───────────────────────────────────────────┐       │
│    │                   SAM                      │       │
│    │       Serviceable Addressable Market      │       │
│    │    "Who we can realistically reach"       │       │
│    │                                           │       │
│    │    ┌───────────────────────────────┐     │       │
│    │    │             SOM               │     │       │
│    │    │   Serviceable Obtainable     │     │       │
│    │    │   "What we can capture"      │     │       │
│    │    └───────────────────────────────┘     │       │
│    └───────────────────────────────────────────┘       │
└─────────────────────────────────────────────────────────┘
```

**Sizing Approaches**

| Approach | Method | Best For |
|----------|--------|----------|
| **Top-down** | Industry reports × market share | Large markets, investor pitches |
| **Bottom-up** | Customers × price × penetration | Validation, realistic planning |
| **Comparable** | Similar company revenue | Benchmarking |

### Bottom-Up Sizing (Most Useful)

**Formula:**
```
Market Size = # of Target Customers × Average Contract Value × Purchase Frequency

Example:
- 50,000 Series A-C startups in US
- × 30% have the problem (15,000)
- × 50% would consider buying (7,500)
- × $5,000 ACV
- × 1 purchase per year
= $37.5M SOM
```

**Refine with Segments:**

| Segment | Count | Problem % | Buy % | ACV | SOM |
|---------|-------|-----------|-------|-----|-----|
| Series A (20-50 emp) | 30,000 | 25% | 40% | $3,000 | $9M |
| Series B (50-200 emp) | 15,000 | 40% | 50% | $6,000 | $18M |
| Series C (200-500 emp) | 5,000 | 50% | 60% | $15,000 | $22.5M |
| **Total** | | | | | **$49.5M** |

### Opportunity Scoring Framework

**RICE Scoring**

| Factor | Description | How to Estimate |
|--------|-------------|-----------------|
| **R**each | How many customers affected? | Data + interviews |
| **I**mpact | How much will it improve outcomes? | 0.25 (low) to 3 (massive) |
| **C**onfidence | How sure are you? | % based on evidence |
| **E**ffort | Person-months to build | Engineering estimate |

**Score = (Reach × Impact × Confidence) / Effort**

**Example:**

| Opportunity | Reach | Impact | Confidence | Effort | Score |
|-------------|-------|--------|------------|--------|-------|
| Real-time collab | 5,000 | 2 | 80% | 4 | 2,000 |
| API access | 2,000 | 2 | 90% | 2 | 1,800 |
| Dark mode | 8,000 | 0.5 | 95% | 1 | 3,800 |
| Mobile app | 3,000 | 1 | 70% | 6 | 350 |

### Opportunity-Solution Tree

**Map Problems to Potential Solutions**

```
OBJECTIVE: Increase activation rate

├── OPPORTUNITY: Users don't understand value
│   ├── Solution: Interactive onboarding
│   ├── Solution: Value-focused empty states
│   └── Solution: Personalized setup flow
│
├── OPPORTUNITY: Setup is too complex
│   ├── Solution: One-click templates
│   ├── Solution: Import from competitors
│   └── Solution: AI-assisted setup
│
└── OPPORTUNITY: Users don't reach "aha moment"
    ├── Solution: Guided first task
    ├── Solution: Sample data to play with
    └── Solution: Success milestone celebrations
```

### Prioritization Matrices

**Impact vs Effort (2x2)**

```
HIGH IMPACT
    │
    │   Quick Wins      │    Big Bets
    │   (Do now)        │    (Plan carefully)
    │                   │
────┼───────────────────┼───────────────────
    │                   │
    │   Fill-ins        │    Money Pits
    │   (Do if easy)    │    (Avoid)
    │                   │
    └───────────────────┴──────────── HIGH EFFORT
```

**ICE Scoring (Simplified)**

| Factor | Description | Scale |
|--------|-------------|-------|
| **I**mpact | Effect on goal | 1-10 |
| **C**onfidence | Evidence strength | 1-10 |
| **E**ase | Effort to implement | 1-10 |

Score = (Impact + Confidence + Ease) / 3

### Customer Value vs Business Value

**Balance Both Perspectives**

| Opportunity | Customer Value | Business Value | Combined |
|-------------|----------------|----------------|----------|
| Pain severity (1-10) | 8 | - | - |
| Frequency (1-10) | 6 | - | - |
| WTP (1-10) | 7 | - | - |
| Revenue potential | - | 8 | - |
| Retention impact | - | 9 | - |
| Strategic fit | - | 7 | - |
| **Total** | **21** | **24** | **45** |

### Validation Before Prioritization

**Evidence Levels**

| Level | Evidence Type | Confidence |
|-------|--------------|------------|
| 1 | Team opinion | 20% |
| 2 | Sales/support feedback | 40% |
| 3 | Qualitative interviews (5+) | 60% |
| 4 | Survey data (100+ responses) | 75% |
| 5 | Behavioral data (actual usage) | 85% |
| 6 | Experiment results (A/B test) | 95% |

**Minimum Evidence by Effort**

| Effort | Minimum Evidence Level | Rationale |
|--------|------------------------|-----------|
| < 1 week | Level 2 | Low risk, can learn quickly |
| 1-4 weeks | Level 3 | Need some validation |
| 1-3 months | Level 4 | Significant investment |
| > 3 months | Level 5-6 | High risk, need strong signals |

### Portfolio Approach

**Balance Your Bets**

```
70/20/10 Rule:

70% → Core improvements
      Low risk, known value
      Features customers request
      Optimizations, debt reduction

20% → Adjacent bets
      Medium risk, probable value
      New use cases for existing users
      Expansion features

10% → Transformational bets
      High risk, high potential
      New markets, new products
      Big swings
```

### Saying No

**Deprioritization Framework**

When to say no:
```
- Opportunity score too low
- Doesn't serve target segment
- Conflicts with strategy
- Better alternatives exist
- Evidence is weak
- Timing is wrong
```

**How to say no:**
```
1. Acknowledge the request
2. Explain the reasoning
3. Share what you ARE doing
4. Leave door open if things change

Example:
"We've heard this from several customers. Right now, we're
focused on [X] because [evidence/strategy]. We're tracking
this and will revisit in Q3 when we have more data."
```

### Opportunity Tracking

**Opportunity Backlog Template**

| ID | Opportunity | Segment | Evidence | Score | Status |
|----|-------------|---------|----------|-------|--------|
| O-1 | Speed up report generation | Power Users | 8 interviews, 40% mention | 24 | Validating |
| O-2 | Mobile access | Field teams | 3 requests | 12 | Backlog |
| O-3 | Integration with Slack | All | Analytics: 60% use Slack | 28 | Building |
| O-4 | AI-generated insights | Enterprise | 2 enterprise requests | 8 | Watching |

### Anti-Patterns

- **HiPPO prioritization** — Highest Paid Person's Opinion wins
- **Squeaky wheel** — Loudest customer gets priority
- **Recency bias** — Last request heard seems most important
- **Feature factory** — Building without validating outcomes
- **Analysis paralysis** — Scoring forever, building never
- **Single-metric tyranny** — Over-indexing on one factor
- **Ignoring strategic fit** — Building things that don't compound
- **Sunk cost fallacy** — Continuing because you started
