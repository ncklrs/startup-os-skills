---
title: Architectural Significance Assessment
impact: HIGH
tags: readiness, significance, asr-test, prioritization
---

## Architectural Significance Assessment

**Impact: HIGH**

Not every technical decision warrants an ADR. Use the ASR (Architecturally Significant Requirement) test to determine which decisions merit formal documentation. Spend 1-2 minutes per issue assessment — this is a qualitative tool for making tacit knowledge explicit, not a quantitative scoring system.

### The Seven ASR Criteria

Rate each criterion as High, Medium, or Low for the decision under consideration:

| # | Criterion | Description | H/M/L |
|---|-----------|-------------|--------|
| 1 | **Business Impact** | Directly associated with high business value or business risk | |
| 2 | **Stakeholder Concern** | Matters to critical stakeholders (sponsors, compliance, regulators) | |
| 3 | **Quality-of-Service Deviation** | Runtime characteristics that substantially differ from current architecture | |
| 4 | **External Dependencies** | Involves dependencies with unpredictable, unreliable, or uncontrollable behavior | |
| 5 | **Cross-Cutting Nature** | System-wide impact affecting multiple components (security, monitoring, auth) | |
| 6 | **First-of-a-Kind** | Novel implementation the team hasn't previously attempted | |
| 7 | **Historical Precedent** | Similar decisions caused problems, overruns, or dissatisfaction in past projects | |

**Threshold**: If 2+ criteria score High, or 4+ score Medium or above, the decision warrants a formal ADR.

### Decisions That Almost Always Need ADRs

These categories of decisions have consistently high architectural significance:

- Product minimum functionality and regulatory compliance boundaries
- Architectural style selection (monolith, microservices, event-driven)
- Technology stack choices (languages, frameworks, databases)
- Integration approach and API contracts between systems
- Authentication and authorization strategy
- Data ownership and governance models
- Service granularity and bounded context boundaries
- Cloud/edge/on-premise deployment topology

### Good Example

```markdown
## ASR Assessment: Migrate from REST to gRPC for Internal Services

| Criterion              | Rating | Rationale                                            |
|------------------------|--------|------------------------------------------------------|
| Business Impact        | Medium | Performance gains for premium tier users              |
| Stakeholder Concern    | Low    | Internal infrastructure change                       |
| QoS Deviation          | High   | Changes latency profile, serialization, streaming    |
| External Dependencies  | Medium | gRPC toolchain maturity varies by language            |
| Cross-Cutting          | High   | Affects all service-to-service communication          |
| First-of-a-Kind        | High   | Team has no gRPC production experience                |
| Historical Precedent   | Medium | Last protocol change caused 3-week rollback           |

**Result: 3 High, 2 Medium → ADR warranted**
```

### Bad Example

```
"We should write an ADR for choosing between tabs and spaces."
→ Not architecturally significant. No business impact, no QoS change,
  no cross-cutting concern. Use a linter config instead.
```

### Checklist

- [ ] Spent 1-2 minutes evaluating each of the seven criteria
- [ ] Rated criteria honestly (High/Medium/Low), not inflated to justify a preference
- [ ] Decision meets threshold (2+ High or 4+ Medium)
- [ ] If borderline, considered whether the decision is easily reversible (reversible → skip ADR)
