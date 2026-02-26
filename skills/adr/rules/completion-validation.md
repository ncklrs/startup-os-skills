---
title: Evidence Gathering and Stakeholder Agreement
impact: MEDIUM-HIGH
tags: completion, validation, evidence, agreement, stakeholders
---

## Evidence Gathering and Stakeholder Agreement

**Impact: MEDIUM-HIGH**

The Evidence and Agreement criteria of ECADR deserve deeper guidance because they are the most commonly skipped steps. Teams often accept decisions without proving they work or confirming alignment.

### Evidence Strategies

Choose the validation method appropriate to the decision's risk level:

| Method | Effort | Confidence | Best For |
|--------|--------|------------|----------|
| **Architectural spike** | High | High | Novel technology, unproven approaches |
| **Proof of concept** | Medium-High | High | Integration viability, performance claims |
| **Expert vouching** | Low | Medium | Well-understood domains, team expertise |
| **Reference architecture** | Low | Medium | Industry-standard patterns |
| **Literature/docs review** | Low | Low-Medium | Vendor claims, compatibility questions |
| **Team evaluation** | Medium | Medium | Familiarity assessment, operational readiness |

### What Good Evidence Looks Like

```markdown
## Validation

### Spike Results (ADR-0011)
- Tested PostgreSQL read replicas with 2M row dataset
- Achieved 7.2ms p99 read latency (requirement: <10ms)
- Cross-region replication lag: 45-80ms (acceptable for read replicas)
- Failover tested: 12-second promotion time

### Operational Readiness
- Team has 4 years PostgreSQL production experience
- Existing monitoring (PgBouncer, pg_stat_statements) transfers directly
- Backup/restore runbook exists from User Service v1

### Known Gaps
- Write scaling beyond 10K/sec not tested (expected Year 2 requirement)
- Multi-region write not validated (would need CockroachDB if required)
```

### What Bad Evidence Looks Like

```markdown
## Validation
We're confident PostgreSQL will work because it's widely used.
The internet says it's good for this kind of workload.
```

This lacks specific measurements, team context, and honest gap analysis.

### Stakeholder Agreement Patterns

**For team-level decisions:**
- Present in team standup or sprint planning
- Capture verbal agreement in the ADR ("Discussed in sprint 14 planning, team agreed unanimously")
- Allow 2-3 day review period for async teams

**For cross-team decisions:**
- Schedule a dedicated review session
- Send ADR draft to all affected teams with explicit review deadline
- Document dissenting opinions and how they were addressed
- Require explicit sign-off from team leads

**For organization-level decisions:**
- Architecture review board or technical leadership review
- Formal presentation with Q&A
- Written approval from designated authority
- Communication plan for rollout

### Handling Disagreement

When stakeholders disagree, document it honestly:

```markdown
## More Information

### Stakeholder Positions
- **Backend team**: Preferred PostgreSQL for operational familiarity
- **SRE team**: Preferred CockroachDB for built-in multi-region support
- **Resolution**: PostgreSQL chosen for Year 1 with explicit migration
  trigger (ADR-0012a) if multi-region writes become a requirement.
  SRE team's concern addressed by scheduling CockroachDB evaluation
  in Q3 if write scaling exceeds projections.
```

### Checklist

- [ ] Validation method chosen appropriate to decision risk level
- [ ] Evidence includes specific measurements or concrete experience, not just opinions
- [ ] Known gaps and assumptions explicitly documented
- [ ] All affected stakeholders have reviewed (not just the author's team)
- [ ] Disagreements documented with resolution approach
- [ ] Agreement captured in the ADR record itself, not just verbal
