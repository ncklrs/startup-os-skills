---
title: MADR Template Structure
impact: CRITICAL
tags: creation, madr, template, format, structure
---

## MADR Template Structure

**Impact: CRITICAL**

Use the Markdown Architectural Decision Record (MADR) template for all ADRs. Consistency across records makes the decision log searchable, reviewable, and maintainable. Every ADR should follow this structure, customizing optional sections as appropriate for the decision's complexity.

### Full Template

```markdown
# ADR-NNNN: [Short Noun Phrase Describing Decision]

## Status
[proposed | accepted | deprecated | superseded by ADR-XXXX]

## Date
YYYY-MM-DD

## Deciders
[Names and roles of decision makers]

## Consulted
[Subject matter experts with two-way communication]

## Informed
[Stakeholders receiving one-way updates after the decision]

## Context and Problem Statement
[1-3 paragraphs explaining the situation. Frame as a question when possible.
Include links to issue trackers, RFCs, or collaboration boards.
Make the reader curious about why this matters.]

## Decision Drivers
- [Quality attribute, business constraint, or technical concern]
- [Each driver should be a concrete, measurable concern when possible]
- [Drivers justify why the criteria matter]

## Considered Options
1. [Option A — list the chosen option first by convention]
2. [Option B]
3. [Option C]

## Decision Outcome
Chosen option: "[Option A]", because [justification referencing
the decision drivers above].

### Consequences
- Good, because [positive consequence for the system/team/users]
- Good, because [another benefit]
- Bad, because [accepted tradeoff or limitation]
- Bad, because [known cost or risk]

## Pros and Cons of Options

### Option A
[Brief description or link to more detail]
- Good, because [advantage]
- Good, because [another advantage]
- Bad, because [disadvantage]
- Neutral, because [neither good nor bad, but worth noting]

### Option B
[Brief description]
- Good, because [advantage]
- Bad, because [disadvantage]
- Bad, because [another disadvantage]

### Option C
[Brief description]
- Good, because [advantage]
- Bad, because [disadvantage]

## Validation
[How will compliance be verified? Code review, design review,
architectural fitness function, spike, load test, etc.]

## More Information
[Links to related ADRs, RFCs, spikes, or external references.
State confidence level and planned review date.
Note any assumptions that could invalidate this decision.]
```

### Minimal Template (MADR Light)

For simpler or lower-impact decisions, use five core sections:

```markdown
# ADR-NNNN: [Short Title]

## Context and Problem Statement
[Brief situation description]

## Decision Drivers
- [Key driver 1]
- [Key driver 2]

## Considered Options
1. [Option A]
2. [Option B]

## Decision Outcome
Chosen option: "[Option A]", because [justification].

### Consequences
- Good, because [benefit]
- Bad, because [tradeoff]
```

### Section Guidance

| Section | Required | Guidance |
|---------|----------|----------|
| Title | Yes | Short noun phrase: "Use PostgreSQL for User Service" not "Database Decision" |
| Status | Yes | Track lifecycle: proposed → accepted → deprecated/superseded |
| Context | Yes | Make readers curious. Frame as a question when possible |
| Drivers | Yes | Concrete criteria, not vague aspirations like "be scalable" |
| Options | Yes | Minimum two realistic alternatives at consistent abstraction levels |
| Outcome | Yes | Name the chosen option explicitly and justify with drivers |
| Consequences | Yes | Both good AND bad — never just benefits |
| Pros/Cons | Recommended | Detailed analysis using "Good/Bad/Neutral, because..." format |
| Validation | Recommended | How you will verify the decision works |
| More Info | Optional | Supporting links, assumptions, review dates |

### Checklist

- [ ] Title is a short noun phrase that describes the decision (not the problem)
- [ ] Status is set (proposed for new, accepted after review)
- [ ] Context frames the problem clearly — a newcomer could understand it
- [ ] At least two decision drivers are listed
- [ ] At least two options are compared at consistent abstraction levels
- [ ] Outcome explicitly names the chosen option with justification
- [ ] Consequences include both positive and negative items
- [ ] Chosen option listed first in the Considered Options list
