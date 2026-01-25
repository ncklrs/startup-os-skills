---
title: Ticket Management & Prioritization
impact: CRITICAL
tags: tickets, prioritization, queue, triage, workflow
---

## Ticket Management & Prioritization

**Impact: CRITICAL**

Effective ticket management is the foundation of support operations. Without proper prioritization and queue management, critical issues get buried, customers wait too long, and agents waste time on low-impact work.

### The Ticket Prioritization Matrix

| Priority | Impact | Urgency | Action |
|----------|--------|---------|--------|
| **P1** | Many users or revenue | Complete block | Immediate all-hands |
| **P2** | Multiple users | Significant block | Next available agent |
| **P3** | Single user | Partial block | Queue position |
| **P4** | Single user | Minor inconvenience | Low priority queue |
| **P5** | Enhancement | Future improvement | Backlog |

### Triage Decision Tree

```
New Ticket Received
        │
        ▼
Is it a system-wide outage?
    YES → P1 Critical → Immediate escalation
    NO  ↓
        ▼
Is revenue or data at risk?
    YES → P2 High → Priority queue
    NO  ↓
        ▼
Is core functionality blocked?
    YES → P3 Medium → Standard queue
    NO  ↓
        ▼
Is it a how-to or feature request?
    YES → P5 Request → Knowledge base + backlog
    NO  → P4 Low → Low priority queue
```

### Good Ticket Prioritization

```
✓ Customer impact determines priority
  → Multiple users affected = higher priority
  → Revenue impact = escalated path
  → Severity based on business impact, not loudness

✓ Clear priority definitions
  → Written criteria everyone understands
  → Examples for each level
  → Edge case guidance

✓ Dynamic reprioritization
  → Tickets age into higher priority
  → Customer tier adjusts SLA
  → Pattern detection for trending issues

✓ Fair queue management
  → First-in-first-out within priority
  → No cherry-picking easy tickets
  → Visibility into all queues

✓ Smart auto-assignment
  → Skill-based routing
  → Workload balancing
  → Customer-agent continuity when helpful
```

### Bad Ticket Prioritization

```
✗ Loudest customer wins
  → Squeaky wheel gets attention
  → Strategic customers ignored

✗ All tickets are P1
  → When everything's urgent, nothing is
  → True emergencies get buried

✗ Manual triage bottleneck
  → Single person assigns all tickets
  → Delays before work begins

✗ Cherry-picking
  → Agents grab easy tickets first
  → Complex issues age indefinitely

✗ No aging escalation
  → Old tickets stay low priority
  → SLA breaches pile up

✗ Priority by customer emotion
  → Angry ≠ urgent
  → Business impact should drive priority
```

### Queue Health Metrics

| Metric | Definition | Target | Warning |
|--------|------------|--------|---------|
| **Backlog Age** | Avg days tickets in queue | <1 day | >3 days |
| **Queue Depth** | Total tickets waiting | Manageable | 3x normal |
| **Priority Distribution** | % in each priority | P1<5%, P2<15% | P1>10% |
| **Wait Time** | Time until first response | Per SLA | Approaching SLA |
| **Agent Utilization** | Time on tickets vs available | 70-80% | <60% or >90% |

### Ticket Assignment Models

| Model | How It Works | Best For |
|-------|--------------|----------|
| **Round-robin** | Next agent in rotation | Equal skill levels |
| **Skill-based** | Match ticket type to expertise | Specialized teams |
| **Load-balanced** | Route to lowest backlog | Uneven workloads |
| **Customer-owned** | Same agent for account | Relationship-based |
| **Swarming** | Team collaborates on ticket | Complex issues |

### Ticket Field Requirements

| Field | Required? | Purpose |
|-------|-----------|---------|
| **Priority** | Yes | SLA and queue position |
| **Category** | Yes | Routing and reporting |
| **Customer** | Yes | Context and SLA tier |
| **Product/Feature** | Yes | Specialist routing |
| **Channel** | Auto | Response expectations |
| **Assignee** | Auto/Yes | Accountability |
| **Status** | Yes | Workflow tracking |

### Automation Opportunities

| Trigger | Action | Benefit |
|---------|--------|---------|
| Keyword in subject | Auto-categorize | Faster triage |
| Customer tier lookup | Set priority modifier | SLA compliance |
| Similar recent ticket | Suggest solution | Faster resolution |
| Idle for X hours | Alert or reassign | Prevent aging |
| Sentiment detected angry | Flag for supervisor | Proactive save |
| Known issue match | Link to parent ticket | Avoid duplicates |

### Ticket Tagging Strategy

```
Good Tags:
├── Product area (auth, billing, integrations)
├── Issue type (bug, how-to, feature-request)
├── Root cause (user-error, product-bug, documentation)
├── Outcome (resolved, known-issue, feature-logged)
└── Customer segment (enterprise, startup, trial)

Bad Tags:
├── Agent names
├── One-time-use tags
├── Overlapping meanings
├── Free-form text
└── Too granular (hundreds of rarely-used tags)
```

### Queue Management Checklist

```
Daily Queue Review:
□ Check P1/P2 tickets first
□ Review aged tickets (>24 hours)
□ Identify trending issues
□ Reassign from OOO agents
□ Balance workload across team

Weekly Queue Review:
□ Analyze backlog trends
□ Review priority accuracy
□ Check for stuck tickets
□ Identify training needs
□ Update automation rules
```

### Anti-Patterns

- **Priority inflation** — Everything marked P1 to get attention faster
- **Queue hiding** — Tickets moved to personal views, invisible to team
- **Status limbo** — Tickets sit "in progress" without updates
- **Duplicate sprawl** — Same issue creates multiple tickets
- **Tag chaos** — Inconsistent or excessive tagging
- **Assignment hoarding** — Agents claim more than they can handle
- **Triage delay** — New tickets sit unassigned too long
