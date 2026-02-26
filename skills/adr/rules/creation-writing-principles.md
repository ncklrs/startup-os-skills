---
title: Seven Good Practices for ADR Authorship
impact: HIGH
tags: creation, writing, quality, best-practices
---

## Seven Good Practices for ADR Authorship

**Impact: HIGH**

These principles distinguish useful ADRs from bureaucratic checkbox exercises. An ADR should read like an executive summary — factual, balanced, and actionable.

### 1. Prioritize by Architectural Significance

Focus ADR effort on decisions with meaningful consequences. Use the ASR test to triage. Not every technical choice needs a record — reserve ADRs for decisions that affect system structure, quality attributes, or cross-cutting concerns.

### 2. Capture Decisions at the Right Time

Don't defer high-impact decisions. Costly-to-reverse choices (database systems, programming languages, architectural styles) require immediate documentation. The cost of delay grows exponentially for decisions that constrain future options.

### 3. Weight Meta-Qualities Appropriately

Prioritize observable, testable qualities (latency, throughput, error rates) over speculative long-term goals ("future scalability"). Avoid over-engineering for hypothetical requirements. Ground quality attributes in current evidence and measurable thresholds.

### 4. Ground in Requirements and Experience

Maintain objectivity. Document your team's actual experience, not vendor marketing claims. Acknowledge personal biases honestly — reviewers respect candor about "we chose X because our team has 3 years of X experience" over manufactured objectivity.

### 5. Invest in Editorial Quality

ADRs are read more often than they are written. Invest in clear writing:
- Apply Ockham's Razor — remove unnecessary adjectives and adverbs
- Right-size the document (one slide may suffice; complex decisions may need several pages)
- Use domain vocabulary consistently
- Write assertively and factually, appropriate for journals and contracts

### 6. Stage Complex Decisions

For multifaceted problems, create staged ADRs:
- **Short-term**: What compromise do we accept now?
- **Mid-term**: What solution do we target within 6 months?
- **Long-term**: What is the ideal end state?

Each stage has time-sensitive justifications. This prevents "boil the ocean" ADRs that try to solve everything at once.

### 7. Disclose Confidence Levels

Express uncertainty honestly. Use explicit confidence markers:

```markdown
## More Information
**Confidence**: Medium — based on spike results with synthetic data.
Production load may reveal different bottlenecks.
**Review date**: After first production month (2025-04-15).
```

### Good Example

```markdown
## Decision Outcome
Chosen option: "PostgreSQL with read replicas", because it satisfies
our <10ms p99 read latency requirement (validated in spike ADR-0011),
the team has 4 years of PostgreSQL operational experience, and
multi-region read replicas address our DR requirements without
introducing eventual consistency for financial transactions.

### Consequences
- Good, because read replicas provide horizontal read scaling
- Good, because strong consistency model prevents financial data anomalies
- Bad, because write scaling is limited to vertical scaling of primary
- Bad, because cross-region replication adds 50-100ms write latency
```

### Bad Example

```markdown
## Decision Outcome
Chosen option: "PostgreSQL", because it's the best database and
everyone uses it. It's fast, reliable, scalable, and free.
There are no real downsides.
```

This violates principles 4 (not grounded in specific requirements), 5 (lazy writing), and 7 (false confidence — no database has "no real downsides").

### Checklist

- [ ] Decision is architecturally significant (not trivial)
- [ ] Captured at the Most Responsible Moment (not prematurely or retroactively)
- [ ] Quality attributes are measurable, not aspirational
- [ ] Claims grounded in evidence or experience, not vendor marketing
- [ ] Writing is concise, factual, and assertive
- [ ] Complex decisions staged into short/mid/long-term phases
- [ ] Confidence level and review date explicitly stated
