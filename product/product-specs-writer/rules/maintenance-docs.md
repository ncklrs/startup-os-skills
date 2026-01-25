---
title: Documentation Maintenance
impact: MEDIUM
tags: maintenance, versioning, deprecation, lifecycle, documentation
---

## Documentation Maintenance

**Impact: MEDIUM**

Documentation that's not maintained becomes worse than no documentation — it actively misleads. Establish clear processes for keeping specs current, versioning changes, and deprecating outdated content.

### Documentation Lifecycle

```
┌─────────┐    ┌─────────┐    ┌─────────┐    ┌─────────┐    ┌─────────┐
│  Draft  │───▶│ Review  │───▶│ Active  │───▶│  Stale  │───▶│ Archived│
└─────────┘    └─────────┘    └─────────┘    └─────────┘    └─────────┘
     │              │              │              │              │
  Writing       Feedback      In Use         Outdated       Historical
  in progress   & approval    reference      needs update   reference only
```

### Document Status System

Every spec document should have a status:

| Status | Badge | Meaning | Action Required |
|--------|-------|---------|-----------------|
| **Draft** | `[DRAFT]` | Work in progress | Do not rely on |
| **Review** | `[REVIEW]` | Ready for feedback | Provide feedback by date |
| **Active** | None | Current, accurate | Use as reference |
| **Needs Update** | `[NEEDS UPDATE]` | Known to be outdated | Update before using |
| **Deprecated** | `[DEPRECATED]` | Being phased out | See replacement doc |
| **Archived** | `[ARCHIVED]` | Historical only | Do not use |

### Documentation Header Template

```markdown
---
title: [Document Title]
status: active
version: 1.2.0
last_updated: 2024-01-15
owner: @username
reviewers: @reviewer1, @reviewer2
related_docs:
  - [PRD: Feature Name](link)
  - [Technical Spec](link)
---

# Document Title

> **Status:** Active
> **Version:** 1.2.0
> **Last Updated:** January 15, 2024
> **Owner:** Product Team (@username)

## Changelog

| Version | Date | Author | Changes |
|---------|------|--------|---------|
| 1.2.0 | 2024-01-15 | @username | Added mobile specs |
| 1.1.0 | 2024-01-10 | @username | Updated error handling |
| 1.0.0 | 2024-01-05 | @username | Initial release |
```

### Versioning Strategy

**Semantic Versioning for Docs:**

| Version | When to Bump | Example Change |
|---------|--------------|----------------|
| **Major** (X.0.0) | Breaking changes, major restructure | Completely new approach |
| **Minor** (x.Y.0) | New sections, significant additions | Added API section |
| **Patch** (x.y.Z) | Corrections, clarifications | Fixed typo, updated date |

**When to Create New Version vs. Update:**
- Same document: Minor clarifications, corrections
- New version: Significant changes to approach or scope
- New document: Completely different feature or requirement

### Review Schedule

| Document Type | Review Frequency | Trigger Events |
|---------------|------------------|----------------|
| PRD | Per milestone | Scope change, pivot |
| Technical Spec | Per release | Architecture change |
| API Spec | Per version | Breaking changes |
| User Stories | Per sprint | Refinement changes |
| Runbooks | Quarterly | Incident learnings |
| Style Guides | Semi-annually | Design system updates |

### Documentation Review Checklist

```markdown
## Quarterly Doc Review: [Document Name]

**Reviewer:** @username
**Review Date:** 2024-01-15
**Document Version:** 1.2.0

### Accuracy Check
- [ ] All links work (no 404s)
- [ ] Code examples still work
- [ ] Screenshots match current UI
- [ ] Referenced features still exist
- [ ] Metrics/numbers are current

### Completeness Check
- [ ] Covers current scope (nothing major missing)
- [ ] Edge cases still relevant
- [ ] Error handling still accurate
- [ ] Integration points current

### Relevance Check
- [ ] Still serving its purpose
- [ ] Audience still needs this
- [ ] Not superseded by another doc

### Action Items
- [ ] [List specific updates needed]
- [ ] [Assign owners and dates]

### Verdict
- [ ] **Active:** No changes needed
- [ ] **Needs Update:** Specific updates identified
- [ ] **Deprecate:** Superseded or no longer needed
```

### Deprecation Process

When a document is being retired:

```markdown
# [DEPRECATED] Original Document Title

> **DEPRECATED:** This document is no longer maintained.
> **Reason:** Replaced by [New Document Title](link)
> **Deprecated Date:** January 15, 2024
> **Removal Date:** April 15, 2024

---

## Why This Was Deprecated

[Brief explanation of why this document is being phased out]

## Migration Guide

| Old Concept | New Location | Notes |
|-------------|--------------|-------|
| Section A | [New Doc, Section X](link) | Mostly unchanged |
| Section B | Removed | No longer applicable |
| Section C | [Different Doc](link) | Significantly updated |

## Original Content Below

[Keep original content for reference during transition period]
```

### Documentation Debt Indicators

**Signs your docs are becoming tech debt:**

| Indicator | Red Flag | Action |
|-----------|----------|--------|
| Age | No updates in 6+ months | Schedule review |
| Accuracy | Known inaccuracies not fixed | Prioritize fix |
| Completeness | Major sections marked "TBD" | Complete or remove |
| Relevance | Feature was deprecated | Archive doc |
| Ownership | No clear owner | Assign owner |
| Usage | No views in 3 months | Consider archiving |
| Feedback | Repeated questions about same topic | Improve clarity |

### Documentation Maintenance Automation

**Automated Checks:**

| Check | Frequency | Alert |
|-------|-----------|-------|
| Broken links | Weekly | Slack notification |
| Stale docs (no updates in X days) | Monthly | Email to owner |
| Orphaned docs (no links to them) | Quarterly | Review queue |
| Missing owners | On change | Block merge |
| Expired review dates | Daily | Reminder notification |

**Suggested Tooling:**
- Link checkers: Built into most doc platforms
- Freshness tracking: Custom metadata + scripts
- Analytics: Doc platform analytics or custom
- Ownership: CODEOWNERS-style files for docs

### Good Documentation Maintenance Example

```markdown
# Documentation Maintenance Log: Workspace Sharing

## Active Documents

| Document | Version | Last Updated | Next Review | Owner |
|----------|---------|--------------|-------------|-------|
| PRD | 2.1.0 | 2024-01-15 | 2024-04-15 | @pm |
| Tech Spec | 1.3.0 | 2024-01-10 | 2024-02-10 | @eng |
| API Spec | 1.0.0 | 2024-01-05 | 2024-04-05 | @eng |
| Runbook | 1.1.0 | 2024-01-12 | 2024-04-12 | @sre |

## Recent Changes

### January 2024

**PRD v2.1.0 (Jan 15)**
- Added mobile sharing flow requirements
- Updated success metrics based on beta learnings
- Removed deprecated "public link" references

**Tech Spec v1.3.0 (Jan 10)**
- Updated architecture diagram with caching layer
- Added performance optimization section
- Fixed incorrect database schema

**Runbook v1.1.0 (Jan 12)**
- Added troubleshooting for invitation email delays
- Updated escalation contacts

## Upcoming Reviews

- [ ] Tech Spec review due Feb 10 (@eng)
- [ ] Quarterly PRD review due Apr 15 (@pm)

## Archived Documents

| Document | Archived Date | Reason | Replacement |
|----------|---------------|--------|-------------|
| Sharing RFC | 2024-01-01 | Converted to spec | Tech Spec v1.0 |
| Design Brief | 2024-01-05 | Incorporated into PRD | PRD Section 5 |

## Open Documentation Debt

| Item | Priority | Owner | Due |
|------|----------|-------|-----|
| Add mobile examples to API spec | Medium | @eng | Jan 31 |
| Update screenshots for new UI | Low | @design | Feb 15 |
```

### Bad Documentation Maintenance Example

```markdown
# Sharing Feature Docs

Last updated: sometime last year probably

See:
- sharing-spec.doc (on someone's machine)
- the wiki page (not sure which one)
- ask Jake, he knows

TODO: update this
```

**Why it fails:**
- No version control
- No clear locations
- No ownership
- No review process
- Uncertain accuracy

### Documentation Cleanup Rituals

**Monthly:**
- Review "Needs Update" tagged docs
- Check for broken links
- Update stale screenshots

**Quarterly:**
- Full review of active docs
- Archive completed project docs
- Update documentation index

**Per Release:**
- Update version numbers
- Add changelog entries
- Review all referenced docs

**Per Project Completion:**
- Archive project-specific docs
- Extract learnings into permanent docs
- Update style guides if patterns emerged

### Anti-Patterns

- **Write once, read never** — Docs created and forgotten
- **Sacred documents** — Fear of updating "official" docs
- **Tribal knowledge** — "Everyone knows" instead of documenting
- **Documentation sprawl** — Same info in multiple places
- **Perfectionism paralysis** — Not publishing until perfect
- **Owner orphans** — Docs without assigned maintainers
- **Fake freshness** — Updating date without actual review
- **Archive aversion** — Keeping outdated docs "just in case"
- **Review theater** — Marking reviewed without actually reading
- **Wiki wilderness** — No structure, search is only navigation
