---
title: Implementation Project Management
impact: CRITICAL
tags: implementation, project-management, milestones, configuration, data-migration
---

## Implementation Project Management

**Impact: CRITICAL**

Implementation is where onboarding plans become reality. Poor project management is the #1 cause of delayed go-lives and customer frustration. Structured, transparent, and adaptive management separates successful implementations from failures.

### Implementation Project Phases

```
DISCOVERY → DESIGN → BUILD → VALIDATE → DEPLOY → OPTIMIZE
    ↓          ↓        ↓        ↓         ↓          ↓
  Gather    Define   Execute   Test     Launch    Refine
  Reqs      Config   Setup    QA       Go-Live   Iterate
```

### Phase Breakdown

| Phase | Duration | Key Activities | Deliverables |
|-------|----------|----------------|--------------|
| **Discovery** | Week 1-2 | Requirements, current state | Requirements doc |
| **Design** | Week 2-3 | Configuration design, mapping | Design document |
| **Build** | Week 3-5 | Setup, config, integration | Configured system |
| **Validate** | Week 5-6 | Testing, UAT, training | Test results, trained users |
| **Deploy** | Week 6-7 | Pilot, go-live, stabilize | Production system |
| **Optimize** | Week 7+ | Refinement, expansion | Optimization plan |

### Project Plan Template

```
## [Customer Name] Implementation Plan

### Overview
- **Go-Live Target:** [Date]
- **Project Manager:** [Name]
- **Executive Sponsor:** [Name]
- **Working Team:** [Names and roles]

### Phase 1: Discovery (Week 1-2)
| Task | Owner | Due | Status |
|------|-------|-----|--------|
| Current state documentation | Customer | W1D3 | |
| Requirements gathering | Joint | W1D5 | |
| Data audit | Customer | W2D2 | |
| Integration requirements | Technical | W2D4 | |

### Phase 2: Design (Week 2-3)
| Task | Owner | Due | Status |
|------|-------|-----|--------|
| Configuration design | Vendor | W2D5 | |
| Data mapping | Joint | W3D2 | |
| Integration architecture | Technical | W3D3 | |
| Design sign-off | Customer | W3D5 | |

### Phase 3: Build (Week 3-5)
| Task | Owner | Due | Status |
|------|-------|-----|--------|
| Core configuration | Vendor | W4D3 | |
| Data migration | Joint | W4D5 | |
| Integration setup | Technical | W5D2 | |
| User provisioning | Customer | W5D3 | |

### Phase 4: Validate (Week 5-6)
| Task | Owner | Due | Status |
|------|-------|-----|--------|
| QA testing | Vendor | W5D5 | |
| UAT testing | Customer | W6D3 | |
| Admin training | Vendor | W6D2 | |
| User training | Joint | W6D4 | |

### Phase 5: Deploy (Week 6-7)
| Task | Owner | Due | Status |
|------|-------|-----|--------|
| Pilot launch | Joint | W6D5 | |
| Pilot feedback | Customer | W7D2 | |
| Go-live readiness | Joint | W7D3 | |
| Go-live | Joint | W7D5 | |
```

### RACI Matrix Template

| Activity | Vendor PM | Customer PM | Vendor Tech | Customer Tech | Exec |
|----------|-----------|-------------|-------------|---------------|------|
| Project planning | R, A | C, I | I | I | I |
| Requirements | R | A | C | C | I |
| Configuration | R, A | I | R | C | I |
| Data preparation | I | A | C | R | I |
| Data migration | R | A | R | C | I |
| Integration | R | I | R, A | R | I |
| Testing | R | A | R | R | I |
| Training | R, A | C | R | I | I |
| Go-live approval | I | I | I | I | A |

*R=Responsible, A=Accountable, C=Consulted, I=Informed*

### Good Implementation Practices

```
✓ Clear requirements upfront
  → Document before building
  → Sign-off on scope
  → Parking lot for Phase 2

✓ Regular status communication
  → Weekly written updates
  → Real-time issue visibility
  → No surprises

✓ Risk management
  → Identify risks early
  → Mitigation plans ready
  → Escalation triggers defined

✓ Change control
  → Formal change requests
  → Impact assessment
  → Scope protection

✓ Parallel workstreams
  → Don't serialize unnecessarily
  → Multiple tracks when possible
  → Faster overall timeline
```

### Bad Implementation Practices

```
✗ Scope creep acceptance
  → "Yes" to every request
  → Timeline blown
  → Never reaches go-live

✗ Silent status
  → No news shared
  → Customer assumes worst
  → Trust erodes

✗ Hero dependency
  → One person knows everything
  → Vacation = crisis
  → No documentation

✗ Testing shortcuts
  → "We'll fix it in production"
  → Go-live becomes chaos
  → User confidence destroyed

✗ Big bang go-live
  → Everything at once
  → No rollback plan
  → Risk concentrated
```

### Status Report Template

```
## [Customer Name] Weekly Status Report
**Week of:** [Date]
**Overall Status:** 🟢 On Track / 🟡 At Risk / 🔴 Blocked

### Progress Summary
- Completed: [What was done]
- In Progress: [What's happening]
- Coming Up: [Next week focus]

### Milestone Status
| Milestone | Target | Status | Notes |
|-----------|--------|--------|-------|
| Requirements complete | [Date] | ✅ Done | |
| Configuration complete | [Date] | 🔄 In Progress | 70% |
| Data migration | [Date] | ⏳ Pending | |
| Training complete | [Date] | ⏳ Pending | |
| Go-Live | [Date] | ⏳ Pending | |

### Risks & Issues
| Item | Impact | Status | Owner | Mitigation |
|------|--------|--------|-------|------------|
| [Risk 1] | High | Open | [Name] | [Action] |
| [Issue 1] | Medium | Resolved | [Name] | [Resolution] |

### Decisions Needed
- [ ] [Decision 1] - Owner: [Name], Due: [Date]
- [ ] [Decision 2] - Owner: [Name], Due: [Date]

### Action Items
| Action | Owner | Due | Status |
|--------|-------|-----|--------|
| [Action 1] | [Name] | [Date] | Open |
| [Action 2] | [Name] | [Date] | Complete |

### Next Steps
1. [Immediate next step]
2. [Following step]
```

### Data Migration Framework

| Stage | Activities | Validation |
|-------|------------|------------|
| **Assessment** | Inventory, quality audit | Data assessment report |
| **Mapping** | Source to target mapping | Mapping document sign-off |
| **Preparation** | Cleansing, transformation | Clean data set |
| **Test Migration** | Trial run with subset | Test results review |
| **Validation** | Data verification | Validation checklist |
| **Production** | Full migration | Production sign-off |

### Integration Implementation

| Phase | Activities | Success Criteria |
|-------|------------|------------------|
| **Scope** | Define data flows, frequency | Integration requirements doc |
| **Design** | Architecture, error handling | Technical design approved |
| **Develop** | Build connections, mappings | Working integration |
| **Test** | End-to-end testing | All scenarios pass |
| **Deploy** | Production deployment | Live data flowing |
| **Monitor** | Ongoing health checks | SLA met |

### Risk Management Framework

| Risk Category | Example Risks | Mitigation Strategies |
|---------------|---------------|----------------------|
| **Resource** | Key person unavailable | Cross-training, backups |
| **Technical** | Integration complexity | Early POC, expert involvement |
| **Data** | Poor data quality | Assessment, cleansing sprint |
| **Timeline** | External dependencies | Buffer time, parallel paths |
| **Scope** | Requirement changes | Change control, Phase 2 parking |
| **Adoption** | User resistance | Change management, champions |

### Escalation Matrix

| Level | Trigger | Escalation Path | Response Time |
|-------|---------|-----------------|---------------|
| **1 - Issue** | Task blocked | Project manager | 24 hours |
| **2 - Risk** | Milestone at risk | PM + leads | 48 hours |
| **3 - Crisis** | Go-live at risk | Leadership | Same day |
| **4 - Executive** | Project at risk | Executive sponsors | Immediate |

### Change Request Template

```
## Change Request: [CR-XXX]

**Requested By:** [Name]
**Date:** [Date]
**Priority:** High / Medium / Low

### Change Description
[Detailed description of the change]

### Business Justification
[Why is this change needed?]

### Impact Assessment
- **Timeline Impact:** [X days added/removed]
- **Resource Impact:** [Additional effort required]
- **Cost Impact:** [If applicable]
- **Risk Impact:** [New risks introduced]

### Recommendation
[ ] Approve for current phase
[ ] Defer to Phase 2
[ ] Reject with rationale

### Approval
- [ ] Customer PM: [Name] - [Date]
- [ ] Vendor PM: [Name] - [Date]
- [ ] Sponsor (if major): [Name] - [Date]
```

### Implementation Metrics

| Metric | Target | Calculation |
|--------|--------|-------------|
| **On-time milestone completion** | >90% | Milestones met / Total |
| **Scope change rate** | <10% | CRs approved / Original scope |
| **Issue resolution time** | <48h | Avg time open to resolved |
| **Go-live date accuracy** | Within 1 week | Planned vs actual |
| **Customer satisfaction** | 4.5/5 | Post-implementation survey |

### Anti-Patterns

- **Waterfall rigidity** — No adaptation to reality
- **Scope avoidance** — Every request is "out of scope"
- **Over-documentation** — Process over progress
- **Silent suffering** — Problems not escalated
- **Hero culture** — One person carries project
- **Testing theater** — Checkbox testing, not real validation
- **Big bang deployment** — Everything at once with no fallback
- **Handoff void** — Implementation ends, no one continues
