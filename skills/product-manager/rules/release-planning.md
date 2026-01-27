---
title: Release Planning and Coordination
impact: MEDIUM-HIGH
tags: release, launch, coordination, communication
---

## Release Planning and Coordination

**Impact: MEDIUM-HIGH**

Great releases require orchestration across teams. Plan the release as carefully as you plan the feature.

### Release Types

| Type | Scope | Cadence | Ceremony |
|------|-------|---------|----------|
| **Hotfix** | Critical bug | As needed | None (ship fast) |
| **Patch** | Bug fixes, minor improvements | Weekly | Internal announce |
| **Minor** | New features, improvements | Bi-weekly/Monthly | Demo + changelog |
| **Major** | Significant features, breaking changes | Quarterly | Full launch plan |
| **Launch** | New product, major initiative | As planned | Marketing campaign |

### Release Planning Timeline

```
┌─────────────────────────────────────────────────────────────────┐
│                    MAJOR RELEASE TIMELINE                       │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  T-4 weeks        T-2 weeks        T-1 week        LAUNCH       │
│  ──────────       ──────────       ─────────       ──────       │
│  • Feature        • Code freeze    • Final QA      • Deploy     │
│    complete       • Beta testing   • Launch prep   • Announce   │
│  • Internal       • Docs ready     • Comms ready   • Monitor    │
│    testing        • Training       • Rollback      • Support    │
│  • Stakeholder    • Marketing      • On-call       • Celebrate  │
│    preview          ready            ready                      │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### Release Checklist Template

```markdown
## Release Checklist: [Feature Name] v[X.Y]

### Target Date: [Date]
### Release Owner: [PM Name]
### Engineering Lead: [Name]

---

### Pre-Development
- [ ] Requirements documented and approved
- [ ] Success metrics defined
- [ ] Dependencies identified
- [ ] Stakeholders informed of timeline

### Development Complete (T-2 weeks)
- [ ] All code merged to release branch
- [ ] Unit tests passing (>90% coverage)
- [ ] Integration tests passing
- [ ] Performance benchmarks met
- [ ] Security review completed
- [ ] Accessibility audit passed

### Documentation (T-2 weeks)
- [ ] Help docs updated
- [ ] API documentation updated
- [ ] Changelog drafted
- [ ] Release notes drafted
- [ ] Internal FAQ prepared

### Marketing/Comms (T-1 week)
- [ ] Blog post drafted
- [ ] Email announcement drafted
- [ ] Social media posts scheduled
- [ ] In-app announcement configured
- [ ] Press/analyst briefings scheduled (if applicable)

### Sales Enablement (T-1 week)
- [ ] Sales deck updated
- [ ] Demo script prepared
- [ ] Training session completed
- [ ] Competitive positioning updated

### Support Preparation (T-1 week)
- [ ] Support team trained
- [ ] Known issues documented
- [ ] Escalation path defined
- [ ] FAQ for common questions

### Launch Day
- [ ] Deployment successful
- [ ] Smoke tests passing
- [ ] Monitoring dashboards reviewed
- [ ] Announcements published
- [ ] Team on standby for issues

### Post-Launch (T+1 week)
- [ ] Metrics reviewed vs targets
- [ ] User feedback collected
- [ ] Bugs triaged and prioritized
- [ ] Retrospective scheduled
- [ ] Quick fixes deployed if needed
```

### Coordinating Cross-Functional Launch

| Team | Pre-Launch | Launch Day | Post-Launch |
|------|------------|------------|-------------|
| **Product** | Requirements, coordination | Monitor adoption | Analyze metrics |
| **Engineering** | Build, test, deploy | On-call support | Bug fixes |
| **Design** | Assets, documentation | N/A | Collect feedback |
| **Marketing** | Content, campaigns | Publish announcements | Track engagement |
| **Sales** | Training, materials | Customer outreach | Report feedback |
| **Support** | Training, FAQ | First response | Escalate issues |
| **Legal** | Review compliance | N/A | Document if needed |

### Release Communication Template

**Internal Announcement:**

```markdown
## [Feature Name] Shipping Today

### What's New
Brief description of the feature and why it matters.

### Who It Affects
- Users: [segments affected]
- Teams: [internal teams impacted]

### Key Details
- Available: [date/time, regions]
- Documentation: [link]
- Known issues: [link or "none"]

### What You Need to Do
- **Sales:** Review updated deck [link]
- **Support:** Complete training [link]
- **CS:** Prepare to communicate to [segment]

### Questions?
Reach out to [PM name] in #[channel]
```

**External Announcement:**

```markdown
## Introducing [Feature Name]

We're excited to announce [feature] — [one line value prop].

### What's New
[2-3 bullet points of key capabilities]

### Why We Built This
[1 paragraph on customer problem being solved]

### How to Get Started
[Clear instructions or link]

### Learn More
- Documentation: [link]
- Video walkthrough: [link]
- Webinar signup: [link]

### What's Next
[Tease upcoming enhancements]
```

### Feature Flag Rollout Strategy

| Phase | % Users | Duration | Purpose |
|-------|---------|----------|---------|
| **Canary** | 1% | 1-2 days | Catch critical bugs |
| **Beta** | 5-10% | 3-5 days | Validate at scale |
| **GA Soft** | 25-50% | 1 week | Monitor metrics |
| **GA Full** | 100% | Ongoing | Complete rollout |

```markdown
## Rollout Plan: Feature X

### Phase 1: Canary (1%)
- Target: Internal employees only
- Duration: 2 days
- Exit criteria: No P0/P1 bugs, <1% error rate

### Phase 2: Beta (10%)
- Target: Power users (>10 sessions/week)
- Duration: 5 days
- Exit criteria: NPS > 30, no major UX issues

### Phase 3: GA Soft (50%)
- Target: All paid users
- Duration: 1 week
- Exit criteria: Adoption > 20%, no support spike

### Phase 4: GA Full (100%)
- Target: All users
- Exit criteria: Metrics meet targets

### Rollback Triggers
- P0 bug affecting >1% users
- Error rate >5%
- NPS drop >20 points
- Support tickets 3x baseline
```

### Managing Launch Risks

| Risk | Mitigation | Contingency |
|------|------------|-------------|
| **Critical bug discovered** | Thorough QA, staged rollout | Feature flag off, hotfix |
| **Performance issues** | Load testing, monitoring | Scale infrastructure, disable feature |
| **Negative user reaction** | User research, beta testing | Rapid iteration, rollback |
| **Dependencies not ready** | Early coordination, buffers | Delay or descope |
| **Support overwhelmed** | Training, documentation | All-hands support, hire temp |

### Post-Launch Review Template

```markdown
## Post-Launch Review: [Feature Name]

### Launch Summary
- **Ship date:** [Date]
- **Target audience:** [Segment]
- **Success metrics target:** [Metric + target]

### Results (T+2 weeks)
| Metric | Target | Actual | Status |
|--------|--------|--------|--------|
| Adoption | 25% | 31% | Exceeded |
| NPS | +10 | +8 | Close |
| Support tickets | <100 | 87 | Met |

### What Went Well
- Staged rollout caught bug early
- Sales enablement was effective
- Documentation was comprehensive

### What Could Improve
- Marketing timing was rushed
- Missing edge case in QA
- Stakeholder comms could be earlier

### Action Items
- [ ] Fix bug found in beta (owner: eng)
- [ ] Start earlier on marketing next time (owner: PM)
- [ ] Add edge case to QA checklist (owner: QA)

### Next Steps
- v1.1 planning with feedback incorporated
- Retrospective with full team scheduled
```

### Anti-Patterns

- **Big bang releases** — Shipping everything at once, no rollout plan
- **Surprise launches** — Not coordinating with stakeholders
- **No rollback plan** — Shipping without an escape hatch
- **Documentation afterthought** — Writing docs after launch
- **Ignoring post-launch** — Shipping and moving on immediately
- **Over-engineering launches** — Massive campaigns for small features
- **Under-communicating** — Teams learn about launch from customers
