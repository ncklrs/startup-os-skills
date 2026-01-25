---
title: PRD Writing
impact: CRITICAL
tags: prd, requirements, product, vision, scope
---

## PRD Writing

**Impact: CRITICAL**

A PRD is the single source of truth for what you're building and why. It aligns stakeholders, prevents scope creep, and gives engineering the context they need to make good decisions.

### The PRD Purpose

A PRD answers these questions:
1. **Why** are we building this? (Problem, opportunity)
2. **What** are we building? (Solution, scope)
3. **For whom** are we building? (Users, personas)
4. **How** will we know it works? (Metrics, success criteria)
5. **What** are the constraints? (Timeline, resources, dependencies)

### PRD Structure Framework

| Section | Purpose | Length |
|---------|---------|--------|
| **Executive Summary** | Quick overview for skimmers | 2-3 sentences |
| **Problem Statement** | Why this matters | 1-2 paragraphs |
| **Goals & Success Metrics** | How we measure success | Bulleted list |
| **User Personas** | Who we're building for | 1-2 personas |
| **User Stories** | What users can do | 5-15 stories |
| **Scope** | What's in and out | Two lists |
| **Requirements** | Detailed needs | Categorized list |
| **Constraints** | Limitations and dependencies | Bulleted list |
| **Timeline** | Key milestones | Table or list |
| **Open Questions** | Unresolved decisions | Bulleted list |
| **Appendix** | Supporting research, mocks | As needed |

### Problem Statement Formula

**Template:**
```
[User segment] struggles with [problem] when trying to [goal].
Currently, they [workaround], which results in [pain/cost].
By building [solution], we can [benefit], which will [business impact].
```

### Good PRD Example

```markdown
# PRD: Team Workspace Sharing

## Executive Summary
Enable teams to share workspaces with granular permissions, reducing the
current friction of workspace duplication and manual access management.

## Problem Statement
Teams of 5+ members struggle with workspace collaboration. Currently,
users duplicate workspaces or share account credentials, leading to:
- 40% of support tickets related to access issues
- Average 3.2 duplicate workspaces per team
- Security risk from shared credentials

Customer interviews (n=23) identified this as the #1 requested feature.

## Goals & Success Metrics

**Primary Goal:** Reduce workspace duplication by 60% within 90 days of launch

| Metric | Current | Target | Measurement |
|--------|---------|--------|-------------|
| Duplicate workspaces per team | 3.2 | 1.3 | Analytics |
| Access-related support tickets | 40% | 15% | Zendesk |
| Team collaboration NPS | 32 | 50 | Survey |

**Secondary Goals:**
- Increase team plan upgrades by 25%
- Reduce time-to-collaborate for new team members by 50%

## User Personas

**Primary: Team Lead (Sarah)**
- Manages 5-10 team members
- Needs to control who sees what
- Pain: Spends 2+ hours/week managing access manually

**Secondary: Team Member (Alex)**
- Joins existing teams
- Needs quick access to relevant workspaces
- Pain: Waits 1-2 days for access requests

## User Stories
[See stories-* rules for detailed format]

1. As a team lead, I want to invite members to my workspace so that
   they can collaborate without creating duplicates
2. As a team lead, I want to set permission levels so that I can
   control who can edit vs. view
3. As a team member, I want to see all workspaces shared with me
   so that I can quickly find what I need

## Scope

**In Scope (v1):**
- Workspace invitation by email
- Three permission levels: Owner, Editor, Viewer
- Invitation management (revoke, modify)
- Shared workspace indicator in UI

**Out of Scope (v1):**
- Public/link sharing
- Workspace transfer (change owner)
- Permission inheritance (folders)
- Guest access (external users)

## Requirements

### Functional Requirements
- FR-1: Users can invite up to 50 members per workspace
- FR-2: Invitations expire after 7 days if not accepted
- FR-3: Owners can modify permissions at any time
- FR-4: Members receive email notification on invitation

### Non-Functional Requirements
- NFR-1: Invitation flow completes in <2 seconds
- NFR-2: Permission changes apply within 30 seconds
- NFR-3: Support 1000 concurrent workspace members

## Constraints

**Technical:**
- Must integrate with existing auth system (Auth0)
- Cannot modify current workspace data model significantly

**Business:**
- Must ship before Q3 for enterprise sales push
- Design resources limited to 2 weeks

**Dependencies:**
- Email service capacity increase (Ops team)
- Auth0 plan upgrade for group claims

## Timeline

| Milestone | Date | Deliverable |
|-----------|------|-------------|
| Design complete | June 15 | Figma specs approved |
| API complete | July 1 | Backend ready for integration |
| Beta launch | July 15 | 10% rollout to Teams plan |
| GA launch | August 1 | 100% rollout |

## Open Questions

- [ ] Should free plans have sharing? (Decision: Product leadership)
- [ ] Max members per workspace? (Proposed: 50, pending Eng review)
- [ ] Email template ownership? (Marketing or Product?)

## Appendix

- [Customer interview summary](link)
- [Competitive analysis](link)
- [Design explorations](link)
```

### Bad PRD Example

```markdown
# PRD: Sharing Feature

## Overview
We need to add sharing to workspaces because customers want it.

## Requirements
- Add sharing
- Make it fast
- Should be secure
- Users should like it

## Timeline
ASAP - this is high priority

## Notes
Talk to engineering about what's possible.
```

**Why this fails:**
- No problem statement or business justification
- No success metrics or acceptance criteria
- Vague requirements ("fast", "secure", "like it")
- No scope boundaries — everything is implied
- No user context or personas
- Timeline without milestones

### PRD Review Checklist

Before sharing a PRD, verify:

```
□ Problem is validated with data or research
□ Success metrics are specific and measurable
□ Scope clearly states what's OUT as well as IN
□ All user personas are represented in stories
□ Technical constraints are documented
□ Dependencies are identified with owners
□ Timeline has specific milestones
□ Open questions are explicitly listed
□ Stakeholders are identified for sign-off
```

### PRD Versioning

| Version | Trigger | Documentation |
|---------|---------|---------------|
| Draft | Initial creation | Mark as "[DRAFT]" in title |
| Review | Ready for feedback | Share with stakeholders |
| Approved | Stakeholder sign-off | Record approvers and date |
| Updated | Scope change | Changelog section, version bump |
| Deprecated | Feature shipped/cancelled | Mark as "[ARCHIVED]" |

### Anti-Patterns

- **The Novel** — 30-page PRDs nobody reads. Keep it scannable.
- **The Wishlist** — Everything the customer ever mentioned. Prioritize ruthlessly.
- **The Solution Spec** — Jumping to "how" before establishing "what" and "why"
- **The Orphan** — PRD without clear owner or stakeholders
- **The Frozen Doc** — PRD that never updates as learnings emerge
- **The Assumption Factory** — Missing validation, just "we think" statements
- **The Feature Factory** — Requirements without business outcomes
- **Spec by Jira** — Tickets without the connecting narrative
