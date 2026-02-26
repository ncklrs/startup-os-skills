---
title: Eleven ADR Anti-Patterns
impact: HIGH
tags: creation, anti-patterns, quality, review
---

## Eleven ADR Anti-Patterns

**Impact: HIGH**

These anti-patterns are distilled from Olaf Zimmermann's research into common ADR failures. When reviewing or writing ADRs, check for these problems. They fall into four categories: subjectivity issues, time-dimension problems, structural issues, and deceptive tactics.

### Subjectivity Issues

**1. Fairy Tale**
Shallow justification that presents only benefits without acknowledging tradeoffs or drawbacks. Real engineering decisions always involve costs.

```markdown
# Bad: Fairy Tale
## Consequences
- Good, because microservices are modern and scalable
- Good, because teams can deploy independently
- Good, because we can use the best tool for each job
# Where are the bad consequences?
```

**2. Sales Pitch**
Marketing language, exaggerations, and unsubstantiated claims. ADRs are technical journals, not vendor brochures.

```markdown
# Bad: Sales Pitch
"Kubernetes is the industry-leading, battle-tested, enterprise-grade
platform that will revolutionize our deployment pipeline."
# vs. Good: Factual
"Kubernetes provides container orchestration with automated scaling.
Our team has no production K8s experience, requiring 2-3 months ramp-up."
```

**3. Free Lunch Coupon**
Ignoring difficult consequences, especially long-term operational costs, maintenance burden, and team skill requirements.

**4. Dummy Alternative**
Including an obviously unworkable option to make the preferred solution look better. Every listed alternative must be a genuine candidate that could solve the stated problem.

```markdown
# Bad: Dummy Alternative
## Considered Options
1. Use Redis for caching (our preferred approach)
2. Build a custom caching layer from scratch in assembly
3. Don't use caching at all
# Options 2 and 3 are clearly not real alternatives
```

### Time-Dimension Problems

**5. Sprint**
Considering only one option and only immediate effects. No comparison, no long-term thinking. This is a mandate disguised as a decision.

**6. Tunnel Vision**
Ignoring operational, maintenance, and cross-stakeholder perspectives. A decision that's great for developers but terrible for SREs is not a good decision.

**7. Maze**
Topic-content mismatch with irrelevant detail discussions. The ADR wanders into implementation specifics, tangential research, or unrelated concerns instead of staying focused on the decision.

### Structural Issues

**8. Blueprint or Policy in Disguise**
Cookbook-style documents with step-by-step instructions and commanding tone ("you must", "always do"). ADRs document decisions, not procedures.

**9. Mega-ADR**
Stuffing extensive architectural details, multiple diagrams, code snippets, and exhaustive analysis into a single record. If an ADR exceeds 2-3 pages, it likely needs to be split or it's trying to be an architecture document.

**10. Novel/Epic**
Condensing an entire Software Architecture Document into a single ADR. Each ADR should address one specific decision, not the entire system design.

### Deceptive Tactics

**11. Magic Tricks**
Pseudo-urgency, problem-solution mismatches, or false quantitative precision. This includes weighted scoring matrices without meaningful measurement — assigning numbers to subjective criteria to create an illusion of objectivity.

```markdown
# Bad: Magic Tricks (false precision)
| Criteria    | Weight | Redis | Memcached | PostgreSQL |
|-------------|--------|-------|-----------|------------|
| Performance | 0.35   | 9     | 8         | 5          |
| Reliability | 0.25   | 8     | 6         | 9          |
| Total       |        | 8.65  | 7.10      | 6.60       |
# These numbers are subjective, but the scoring creates false objectivity
```

### Detection Checklist

When reviewing an ADR, check for these red flags:

- [ ] **No negative consequences listed** → Fairy Tale
- [ ] **Superlatives or marketing language** → Sales Pitch
- [ ] **Operational costs not mentioned** → Free Lunch Coupon
- [ ] **An option that nobody would seriously consider** → Dummy Alternative
- [ ] **Only one option evaluated** → Sprint
- [ ] **Only developer perspective considered** → Tunnel Vision
- [ ] **Rambling into unrelated topics** → Maze
- [ ] **Step-by-step instructions instead of rationale** → Blueprint
- [ ] **Exceeds 3 pages with extensive diagrams/code** → Mega-ADR
- [ ] **Covers multiple unrelated decisions** → Novel/Epic
- [ ] **Weighted scoring with subjective numbers** → Magic Tricks
