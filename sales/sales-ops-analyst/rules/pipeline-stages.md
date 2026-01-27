---
title: Pipeline Stages & Velocity
impact: CRITICAL
tags: pipeline, stages, velocity, conversion, forecasting
---

## Pipeline Stages & Velocity

**Impact: CRITICAL**

Pipeline stages tell the story of your deals. Well-defined stages enable accurate forecasting, identify bottlenecks, and create accountability.

### Stage Design Principles

Each stage should have:
1. **Clear entry criteria** — What must happen to enter this stage?
2. **Clear exit criteria** — What must happen to move forward?
3. **Defined probability** — What % of deals at this stage close?
4. **Owner accountability** — Who's responsible for progression?

### Standard B2B SaaS Pipeline

| Stage | Entry Criteria | Exit Criteria | Probability | Avg Time |
|-------|----------------|---------------|-------------|----------|
| **Qualification** | Discovery call completed | BANT confirmed | 10% | 7 days |
| **Discovery** | Pain/need identified | Solution mapped to need | 20% | 14 days |
| **Demo/Evaluation** | Demo scheduled | Technical validation complete | 40% | 21 days |
| **Proposal** | Pricing discussed | Proposal delivered and reviewed | 60% | 14 days |
| **Negotiation** | Verbal agreement | Terms agreed, contract sent | 80% | 14 days |
| **Closed Won** | Contract signed | — | 100% | — |
| **Closed Lost** | Deal lost | Loss reason captured | 0% | — |

### Stage Criteria Documentation

**Good Example: Clear Stage Definition**

```
Stage: Demo/Evaluation
Entry Criteria:
  □ Discovery call completed
  □ At least 2 stakeholders identified
  □ Budget range confirmed ($X - $Y)
  □ Timeline established (decision within 90 days)

Exit Criteria (to Proposal):
  □ Demo delivered to decision maker
  □ Technical requirements validated
  □ Integration feasibility confirmed
  □ Success metrics agreed upon

Exit Criteria (to Closed Lost):
  □ Loss reason selected
  □ Competitor field updated (if applicable)
  □ Follow-up task created (if nurture)

Probability: 40%
Expected Duration: 14-21 days
Red Flag: >30 days in stage
```

**Bad Example: Vague Stage Definition**

```
Stage: Demo
Entry: They want to see a demo
Exit: Demo done
Probability: 50%
Duration: Whenever
```

### Pipeline Velocity Analysis

**Velocity Formula:**
```
Velocity = (Win Rate × Avg Deal Size × # of Opps) / Avg Sales Cycle

Current State:
  25% × $50,000 × 100 opps / 90 days = $13,889/day

Target State (improve win rate):
  30% × $50,000 × 100 opps / 90 days = $16,667/day (+20%)
```

**Stage Conversion Funnel:**

```
Qualification    100 opps ─────────────────────────┐
      │                                            │ 30% drop
      ▼                                            │
Discovery         70 opps ◄────────────────────────┘
      │                                            │ 29% drop
      ▼                                            │
Demo/Eval         50 opps ◄────────────────────────┘
      │                                            │ 40% drop
      ▼                                            │
Proposal          30 opps ◄────────────────────────┘
      │                                            │ 17% drop
      ▼                                            │
Negotiation       25 opps ◄────────────────────────┘
      │                                            │ 0% drop
      ▼                                            │
Closed Won        25 opps ◄────────────────────────┘

Overall Win Rate: 25%
```

### Stage Duration Benchmarks

| Stage | Healthy | Warning | Critical |
|-------|---------|---------|----------|
| Qualification | <7 days | 7-14 days | >14 days |
| Discovery | <14 days | 14-21 days | >30 days |
| Demo/Eval | <21 days | 21-30 days | >45 days |
| Proposal | <14 days | 14-21 days | >30 days |
| Negotiation | <14 days | 14-30 days | >45 days |

### Pipeline Health Metrics

| Metric | Calculation | Target |
|--------|-------------|--------|
| **Coverage Ratio** | Pipeline ÷ Quota | 3-4x |
| **Stage Distribution** | % of opps per stage | Pyramid shape |
| **Aging Rate** | % opps > stage benchmark | <20% |
| **Push Rate** | % opps with changed close date | <30% |
| **Win Rate by Stage** | Wins ÷ Opps entering stage | Increasing |

### Stage Distribution Analysis

**Healthy Pipeline:**
```
Qualification:    ████████████████████ 35%
Discovery:        ███████████████ 25%
Demo/Eval:        ████████████ 20%
Proposal:         ██████ 12%
Negotiation:      ████ 8%
```

**Unhealthy Pipeline (top-heavy):**
```
Qualification:    ███████████████████████████████████ 60%
Discovery:        ███████ 15%
Demo/Eval:        ████ 10%
Proposal:         ███ 8%
Negotiation:      ██ 7%
```

### Validation Rules for Stage Progression

```javascript
// Salesforce validation rule example
// Prevent skipping stages

AND(
  ISCHANGED(StageName),
  NOT(ISPICKVAL(PRIORVALUE(StageName), "Closed Won")),
  NOT(ISPICKVAL(PRIORVALUE(StageName), "Closed Lost")),
  CASE(
    StageName,
    "Discovery", NOT(ISPICKVAL(PRIORVALUE(StageName), "Qualification")),
    "Demo/Evaluation", NOT(OR(
      ISPICKVAL(PRIORVALUE(StageName), "Qualification"),
      ISPICKVAL(PRIORVALUE(StageName), "Discovery")
    )),
    // ... continue for other stages
    false
  )
)
```

### Required Fields by Stage

| Stage | Required Fields |
|-------|----------------|
| Any stage | Account, Amount, Close Date, Owner |
| Discovery+ | Primary Contact, Next Steps |
| Demo+ | Decision Maker, Competition |
| Proposal+ | Proposal Sent Date |
| Negotiation+ | Contract Value |
| Closed Won | Won Reason, Contract Signed Date |
| Closed Lost | Loss Reason, Competitor Won (if applicable) |

### Anti-Patterns

- **Stage inflation** — Reps advance stages without meeting criteria
- **Pipeline stuffing** — Moving unqualified opps to hit coverage targets
- **Close date fiction** — Optimistic dates that constantly push
- **Stage skipping** — Jumping from Discovery to Negotiation
- **Zombie opps** — Deals sitting in stage for months with no activity
- **Probability override** — Manual probability changes without stage change
- **Missing loss reasons** — Closed Lost without capturing why
