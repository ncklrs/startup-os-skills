---
title: Sprint Planning and Backlog Management
impact: HIGH
tags: sprint, backlog, agile, planning, estimation
---

## Sprint Planning and Backlog Management

**Impact: HIGH**

Sprint planning transforms strategy into execution. Great backlog management keeps teams focused, predictable, and shipping value consistently.

### Sprint Planning Process

```
┌─────────────────────────────────────────────────────────────────┐
│                     SPRINT PLANNING FLOW                        │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  BEFORE (PM prep)          DURING (Team)        AFTER (Execute) │
│  ─────────────────         ─────────────        ────────────────│
│  • Groom backlog           • Review capacity    • Daily standups │
│  • Prioritize items        • Commit to work     • Unblock team   │
│  • Write acceptance        • Estimate effort    • Track progress │
│    criteria                • Assign owners      • Manage scope   │
│  • Prepare context         • Flag risks         • Demo + retro   │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### Backlog Health Checklist

| Criteria | Healthy | Unhealthy |
|----------|---------|-----------|
| **Size** | 2-4 sprints of refined work | 100+ unrefined items |
| **Clarity** | Clear acceptance criteria | Vague descriptions |
| **Priority** | Top 20 items stack-ranked | Everything is P1 |
| **Estimates** | Top items estimated | No sizing |
| **Dependencies** | Identified and tracked | Surprise blockers |
| **Mix** | Features + bugs + debt | All features, no maintenance |

### Story Quality Standards

**Good User Story:**

```markdown
## As a marketing manager, I want to export campaign data to CSV
   so that I can analyze performance in my preferred spreadsheet tool

### Acceptance Criteria
- [ ] Export button visible on campaign list page
- [ ] CSV includes: campaign name, dates, spend, impressions, clicks, conversions
- [ ] Export completes in < 30 seconds for up to 1000 campaigns
- [ ] User sees progress indicator during export
- [ ] Error message shown if export fails with retry option

### Technical Notes
- Use existing async job infrastructure
- Rate limit: 5 exports per user per hour

### Out of Scope
- Scheduled/automated exports (future enhancement)
- Custom column selection (v2)

### Size: 5 points
### Dependencies: None
### Designer: @jane (mocks attached)
```

**Bad User Story:**

```markdown
## Export feature

Add export to the campaigns page.
```

**Why this fails:**
- No user context or "why"
- No acceptance criteria
- No scope boundaries
- No technical context

### Estimation Best Practices

**Story Point Scale:**

| Points | Complexity | Example |
|--------|------------|---------|
| **1** | Trivial | Copy change, config update |
| **2** | Simple | Add field, simple validation |
| **3** | Moderate | New component, API endpoint |
| **5** | Complex | Feature with multiple parts |
| **8** | Very complex | Major feature, multiple systems |
| **13** | Epic-level | Consider breaking down |

**Estimation Tips:**
- Compare to reference stories team has completed
- Include testing time, not just coding
- Account for unknowns with spikes
- If > 8 points, break down further

### Sprint Capacity Planning

```markdown
## Sprint 23 Capacity

### Team Composition
- 4 engineers × 10 days = 40 person-days
- Minus: PTO (2 days), meetings (20%), support rotation (10%)
- Available: 40 × 0.7 = 28 person-days

### Velocity Reference
- Last 3 sprints: 32, 28, 35 points
- Average: 32 points
- Commitment: 28-32 points (conservative)

### Allocation
- Features: 70% (20-22 points)
- Bugs: 15% (4-5 points)
- Tech debt: 15% (4-5 points)
```

### Backlog Grooming Agenda

**Weekly grooming session (1 hour):**

```markdown
## Grooming Session - [Date]

### 1. Review upcoming sprint items (20 min)
- Walk through top 10 backlog items
- Clarify requirements, answer questions
- Identify missing information

### 2. Estimate new items (20 min)
- Planning poker for unestimated stories
- Break down items > 8 points
- Add to "ready for sprint" when complete

### 3. Backlog hygiene (10 min)
- Archive stale items (> 6 months untouched)
- Merge duplicates
- Reprioritize based on new information

### 4. Look ahead (10 min)
- Preview items for sprint+2
- Identify research/spikes needed
- Flag dependencies early
```

### Sprint Ceremonies Quick Reference

| Ceremony | Duration | Frequency | Attendees | PM Role |
|----------|----------|-----------|-----------|---------|
| **Planning** | 2 hours | Start of sprint | Dev team | Present priorities, answer questions |
| **Daily standup** | 15 min | Daily | Dev team | Listen, unblock |
| **Grooming** | 1 hour | Weekly | PM + leads | Lead discussion |
| **Demo** | 1 hour | End of sprint | Stakeholders | Facilitate, celebrate |
| **Retro** | 1 hour | End of sprint | Dev team | Participate, take action items |

### Managing Mid-Sprint Changes

| Scenario | Response |
|----------|----------|
| **Critical bug** | Swap equal-sized item out, document trade-off |
| **Executive request** | Assess impact, propose options with trade-offs |
| **Scope creep** | "Great idea, added to backlog for next sprint" |
| **Engineer blocked** | Swarm to unblock, or swap tasks |
| **Undercommitted** | Pull from "stretch" list, not add new |

### Sprint Metrics to Track

| Metric | What It Measures | Target |
|--------|------------------|--------|
| **Velocity** | Points completed per sprint | Consistent (not growing) |
| **Commitment vs. Delivered** | Planning accuracy | > 80% |
| **Carryover** | Incomplete work | < 10% of commitment |
| **Cycle time** | Start to done | Decreasing |
| **Bug escape rate** | Quality | < 5% of stories |

### Anti-Patterns

- **Sprint stuffing** — Committing to more than capacity
- **No commitment** — "We'll see what we get done"
- **Infinite grooming** — Perfecting stories that may never be built
- **Estimation theater** — Going through motions without accuracy
- **Skipping retros** — Missing opportunities to improve
- **PM as ticket writer** — Writing stories without engineering input
- **Velocity as performance metric** — Comparing teams, gaming points
- **No buffer** — Zero slack for unknowns and support
