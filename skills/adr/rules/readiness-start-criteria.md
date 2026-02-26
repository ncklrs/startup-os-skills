---
title: START Criteria for Decision Readiness
impact: CRITICAL
tags: readiness, start, decision-timing, most-responsible-moment
---

## START Criteria for Decision Readiness

**Impact: CRITICAL**

Before writing an ADR, evaluate all five START criteria. An unready decision leads to incomplete records, premature commitments, or wasted effort.

### The Five Criteria

**S — Stakeholders Known**
Decision makers, consulting experts, and affected parties are identified and available to participate. Without the right people, decisions lack authority and buy-in.

**T — Timing (Most Responsible Moment)**
The problem is important and urgent enough that waiting longer would be costly or reduce flexibility. The "Most Responsible Moment" is the last point at which the cost of delay outweighs the benefit of waiting for more information.

**A — Alternatives Identified**
At least two realistic design alternatives have been identified. A single-option "decision" is not a decision — it's a mandate. Each alternative must genuinely address the stated problem.

**R — Requirements and Context Documented**
The problem context, relevant requirements, quality attributes, and decision drivers have been analyzed and recorded. The decision cannot be evaluated without clear criteria.

**T — Template Ready**
An ADR template (MADR or equivalent) has been selected and an empty record created in the decision log.

### Seven Indicators for Early Decisions

Some decisions require earlier attention. Watch for these signals:

1. High architectural significance scores (see ASR test)
2. Substantial financial investment or consequences
3. Extended execution timelines that constrain future options
4. Multiple or unclear downstream dependencies
5. Complex stakeholder negotiations required
6. High abstraction levels that need refinement before implementation
7. Novel problem spaces outside the team's experience

### Good Example

```markdown
## Readiness Check: Database Selection for User Service

- [x] **Stakeholders**: Backend lead (Maya), SRE team (Jorge), Product (Lin) — all confirmed available this sprint
- [x] **Timing**: Schema design starts next sprint; choosing after that constrains migration options
- [x] **Alternatives**: PostgreSQL, DynamoDB, CockroachDB identified as viable candidates
- [x] **Requirements**: Need <10ms p99 reads, multi-region support, strong consistency for financial data
- [x] **Template**: MADR template created as docs/decisions/ADR-0012-user-service-database.md

✅ Ready to proceed with ADR creation.
```

### Bad Example

```markdown
## "Let's just document that we're using Redis"

- [ ] **Stakeholders**: "I think the tech lead is fine with it"
- [ ] **Timing**: "We already deployed it last month"
- [x] **Alternatives**: Only Redis was considered
- [ ] **Requirements**: "It's fast enough"
- [ ] **Template**: No ADR log exists yet

❌ Not ready. This is retroactive justification, not a decision process.
```

### Checklist

- [ ] All decision makers and affected parties identified and available
- [ ] The Most Responsible Moment has arrived (not too early, not too late)
- [ ] At least two genuine alternatives have been identified
- [ ] Problem context, requirements, and decision drivers are documented
- [ ] ADR template selected and empty record created in the log
