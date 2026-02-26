---
title: ADR Lifecycle Management
impact: MEDIUM-HIGH
tags: lifecycle, maintenance, supersede, deprecate, log-management
---

## ADR Lifecycle Management

**Impact: MEDIUM-HIGH**

ADRs are living documents within a decision log. Without active lifecycle management, the log becomes a graveyard of outdated decisions that mislead rather than guide.

### ADR Status Lifecycle

```
proposed → accepted → [active use]
                          ↓
              deprecated (no longer relevant)
                   or
              superseded by ADR-XXXX (replaced by newer decision)
```

| Status | Meaning |
|--------|---------|
| `proposed` | Under review, not yet agreed upon |
| `accepted` | Decision is active and authoritative |
| `deprecated` | Decision is no longer relevant (context changed) |
| `superseded by ADR-XXXX` | Replaced by a newer decision (link to it) |

### File Naming Convention

Use sequential numbering with descriptive titles:

```
docs/decisions/
  ADR-0001-use-madr-template.md
  ADR-0002-monorepo-structure.md
  ADR-0003-postgresql-for-user-service.md
  ADR-0004-event-driven-notifications.md
  ...
```

Alternatively, use date-based prefixes if decisions aren't sequential:

```
docs/decisions/
  2025-01-15-use-madr-template.md
  2025-02-03-monorepo-structure.md
  ...
```

### ADR Log Index

Maintain an index file for quick navigation:

```markdown
# Architecture Decision Log

| ADR | Title | Status | Date |
|-----|-------|--------|------|
| [ADR-0001](ADR-0001-use-madr-template.md) | Use MADR template for decisions | Accepted | 2025-01-15 |
| [ADR-0002](ADR-0002-monorepo-structure.md) | Adopt monorepo structure | Accepted | 2025-02-03 |
| [ADR-0003](ADR-0003-rest-api-style.md) | Use REST for public API | Superseded by ADR-0007 | 2025-02-20 |
| [ADR-0007](ADR-0007-graphql-public-api.md) | Migrate public API to GraphQL | Accepted | 2025-06-10 |
```

### When to Supersede

Create a new ADR (don't edit the old one) when:
- The original context has fundamentally changed
- New alternatives exist that weren't available before
- The original decision proved wrong based on production evidence
- Business requirements shifted enough to invalidate the original drivers

**In the new ADR:**
- Reference the superseded ADR in the Context section
- Explain what changed that necessitates revisiting
- Acknowledge what worked and what didn't about the original decision

**In the old ADR:**
- Update status to `superseded by ADR-XXXX`
- Do NOT delete or substantially edit the original content (it's a historical record)

### Review Triggers

Schedule reviews based on these triggers:

| Trigger | Action |
|---------|--------|
| Planned review date reached | Re-evaluate assumptions and evidence |
| Production incident related to the decision | Assess if decision contributed to failure |
| New team member questions the decision | Good sign — review if rationale still holds |
| Technology landscape shift | Check if new options invalidate current choice |
| Scale threshold exceeded | Review if decision holds at new scale |
| Quarterly architecture review | Scan log for stale or at-risk decisions |

### Linking Related Decisions

ADRs rarely exist in isolation. Document relationships:

```markdown
## More Information

### Related Decisions
- **Depends on**: ADR-0002 (monorepo structure affects deployment)
- **Supersedes**: ADR-0003 (REST API decision)
- **Informs**: ADR-0008 (client SDK generation approach)
- **Conflicts with**: None currently identified
```

### Checklist

- [ ] ADR log index exists and is maintained
- [ ] Sequential numbering or date-based naming is consistent
- [ ] Superseded ADRs link to their replacement (and vice versa)
- [ ] Old ADR content preserved as historical record (not deleted)
- [ ] Review dates and triggers documented for accepted ADRs
- [ ] Related decisions cross-referenced
- [ ] Log reviewed at least quarterly for stale decisions
