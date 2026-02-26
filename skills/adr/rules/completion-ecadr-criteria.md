---
title: ECADR Definition of Done
impact: CRITICAL
tags: completion, ecadr, quality, review, done
---

## ECADR Definition of Done

**Impact: CRITICAL**

Before marking an ADR as "accepted", evaluate all five ECADR criteria. An incomplete ADR creates false confidence — the team thinks a decision was properly made, but gaps in evidence or agreement lead to revisiting it later under worse conditions.

### The Five Criteria

**E — Evidence**
Confirm the chosen design will work:
- Demonstrates it satisfies specific, measurable quality requirements
- Doesn't contradict previous accepted decisions
- Implementable in the short term and maintainable long-term

Validation methods (pick what fits):
- Proof-of-concept or architectural spike
- Expert evaluation or vouching
- Team review with relevant experience
- Reference to similar production systems

**C — Criteria**
At least two alternatives have been identified, investigated, and compared using stakeholder concerns and decision drivers:
- Systematic comparison applied (but pragmatically — avoid over-analysis)
- Tradeoffs between options documented
- Rejected alternatives retained as noted fallbacks where applicable

**A — Agreement**
Sufficient stakeholder alignment achieved:
- Peer/mentor and team have reviewed and concurred
- Involvement level matches decision scope (enterprise decisions need more buy-in)
- Early engagement of stakeholders to prevent later objections
- Stakeholder participation planned in advance, not an afterthought

**D — Documentation**
The decision has been captured and shared:
- Written in MADR or the team's consistent ADR format
- Includes convincing rationale referencing evidence and criteria
- Published in an accessible location (repo, wiki, collaboration tool)
- Announced to all affected parties

**R — Realization and Review Plan**
Implementation and evaluation are scheduled:
- Confirm implementation work is in the backlog or scheduled
- Define when to verify the decision worked as intended
- Plan review timing (sprint retrospective, ATAM session, quarterly review)
- Document triggers for revisiting the decision (assumptions that could change)

### Quick Completion Check

Answer "yes" to all five questions:

1. Is there sufficient confidence the design will work? **(Evidence)**
2. Were at least two options compared systematically? **(Criteria)**
3. Have relevant stakeholders reviewed and aligned? **(Agreement)**
4. Has the decision been documented and shared? **(Documentation)**
5. Are implementation and review tasks scheduled? **(Realization)**

If any answer is "no", either complete that criterion or document why it doesn't apply before proceeding.

### Good Example

```markdown
## Completion Check: ADR-0012 PostgreSQL for User Service

- [x] **Evidence**: Spike in ADR-0011 demonstrated <8ms p99 reads with
      production-like data volume (2M rows). No conflicts with existing
      ADRs (checked ADR-0003, ADR-0007).
- [x] **Criteria**: PostgreSQL, DynamoDB, and CockroachDB compared across
      latency, consistency, operational familiarity, and cost.
- [x] **Agreement**: Backend team reviewed in sprint planning. SRE team
      confirmed operational readiness. Product approved timeline impact.
- [x] **Documentation**: ADR-0012 published in docs/decisions/, announced
      in #architecture Slack channel.
- [x] **Realization**: Migration ticket PROJ-456 created in sprint 14.
      Review scheduled for sprint 18 retrospective. Revisit triggers:
      if write throughput exceeds 10K/sec or if we expand beyond 2 regions.

✅ ADR-0012 is done. Status changed to "accepted".
```

### Scaling Effort to Impact

| Decision Type | Evidence Needed | Agreement Scope | Review Cycle |
|--------------|-----------------|-----------------|--------------|
| Strategic (buy/build/rent) | Spike + cost analysis + expert review | Leadership + all affected teams | Quarterly |
| Tactical (library choice) | Team evaluation + docs review | Team lead + affected developers | Sprint retro |
| Operational (config approach) | Documented team experience | Team consensus | As-needed |

### Checklist

- [ ] Evidence exists that the chosen design satisfies requirements
- [ ] At least two alternatives were compared using documented criteria
- [ ] Relevant stakeholders have reviewed and agreed
- [ ] ADR is written, published, and announced to affected parties
- [ ] Implementation work is scheduled and review triggers are defined
