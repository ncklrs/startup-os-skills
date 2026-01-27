---
title: Cross-Functional Collaboration
impact: HIGH
tags: collaboration, teamwork, design, engineering, communication
---

## Cross-Functional Collaboration

**Impact: HIGH**

PMs don't build products — teams do. Your job is to create the conditions for teams to do their best work together.

### The Product Trio Model

```
┌─────────────────────────────────────────────────────────────────┐
│                                                                 │
│                      ┌─────────────┐                            │
│                      │   PRODUCT   │                            │
│                      │   MANAGER   │                            │
│                      └──────┬──────┘                            │
│                             │                                   │
│              Discovery ─────┼───── Delivery                     │
│                             │                                   │
│             ┌───────────────┴───────────────┐                   │
│             │                               │                   │
│      ┌──────┴──────┐                 ┌──────┴──────┐            │
│      │   PRODUCT   │                 │ ENGINEERING │            │
│      │   DESIGNER  │◄───────────────▶│    LEAD     │            │
│      └─────────────┘                 └─────────────┘            │
│                                                                 │
│                     Shared ownership of                         │
│                   problems AND solutions                        │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### RACI for Common Activities

| Activity | PM | Design | Eng Lead | Engineering |
|----------|:--:|:------:|:--------:|:-----------:|
| Problem definition | A | C | C | I |
| User research | C | A | I | I |
| Solution exploration | C | A | C | I |
| Technical feasibility | C | I | A | C |
| Requirements | A | C | C | I |
| Design specs | C | A | I | C |
| Technical specs | I | I | A | C |
| Implementation | I | C | A | R |
| QA/Testing | C | C | A | R |
| Launch decision | A | C | C | I |
| Success measurement | A | C | C | I |

**Legend:** R=Responsible, A=Accountable, C=Consulted, I=Informed

### Working with Engineering

**What engineers need from PMs:**

| Need | What It Looks Like |
|------|-------------------|
| **Context, not tickets** | "Here's the problem and why it matters" |
| **Clear priorities** | "This is #1, that's #2, period" |
| **Stable requirements** | Minimize mid-sprint changes |
| **Technical respect** | Trust their estimates and approaches |
| **Shielding** | Handle stakeholder management, not them |
| **Autonomy** | Define what, let them figure out how |

**What PMs need from engineers:**

| Need | What It Looks Like |
|------|-------------------|
| **Honest estimates** | Realistic timelines, not optimistic |
| **Early warnings** | Flag risks as soon as seen |
| **Trade-off options** | "We can do X in 2 weeks or Y in 1" |
| **Technical education** | Help PM understand constraints |
| **Solution partnership** | Brainstorm, don't just execute |

### Working with Design

**What designers need from PMs:**

| Need | What It Looks Like |
|------|-------------------|
| **Problem space** | Clear problem definition, not solution |
| **User context** | Access to research, personas, data |
| **Design time** | Space to explore before committing |
| **Constraints upfront** | Technical limitations early |
| **Feedback culture** | Critique design, not designer |

**What PMs need from designers:**

| Need | What It Looks Like |
|------|-------------------|
| **User advocacy** | Push back on bad UX decisions |
| **Multiple options** | Explore before converging |
| **Feasibility awareness** | Consider technical constraints |
| **Iteration willingness** | Adapt based on feedback |
| **Clear handoffs** | Specs engineers can build from |

### Product Trio Rituals

| Ritual | Frequency | Duration | Purpose |
|--------|-----------|----------|---------|
| **Discovery sync** | 2x/week | 30 min | Align on problem space |
| **Design review** | Weekly | 1 hour | Review explorations, give feedback |
| **Backlog grooming** | Weekly | 1 hour | Refine upcoming work |
| **Sprint planning** | Bi-weekly | 2 hours | Commit to sprint work |
| **Retrospective** | Bi-weekly | 1 hour | Improve how we work |

### Healthy vs Unhealthy Team Dynamics

| Dimension | Healthy | Unhealthy |
|-----------|---------|-----------|
| **Ownership** | Shared problems | PM owns requirements, eng executes |
| **Communication** | Direct, transparent | Through tickets only |
| **Feedback** | Given and received openly | Avoided or defensive |
| **Decisions** | Collaborative, PM tie-break | PM dictates, or endless debate |
| **Conflict** | Healthy disagreement | Passive-aggressive or explosive |
| **Trust** | Assumed good intent | Blame and cover-up |
| **Learning** | Retros lead to change | Same problems repeat |

### Managing Conflict Productively

**Conflict Resolution Framework:**

```
1. ACKNOWLEDGE
   "I see we have different views on this."

2. UNDERSTAND
   "Help me understand your perspective better."

3. FIND COMMON GROUND
   "We both want [shared goal]. Let's start there."

4. GENERATE OPTIONS
   "What are all the ways we could approach this?"

5. DECIDE TOGETHER
   "Given our constraints, I propose... What do you think?"

6. COMMIT
   "Let's all support this decision once made."
```

### Cross-Functional Meeting Templates

**Discovery Kickoff:**

```markdown
## Discovery Kickoff: [Problem Area]

### Attendees
Product Trio + [other relevant stakeholders]

### Agenda

1. Problem framing (10 min)
   - What problem are we solving?
   - Who has this problem?
   - Why does it matter now?

2. What we know (15 min)
   - Existing research
   - Quantitative data
   - Competitive landscape

3. What we don't know (10 min)
   - Open questions
   - Assumptions to validate

4. Discovery plan (20 min)
   - Research activities
   - Timeline
   - Owners

5. Success criteria (5 min)
   - How do we know we're ready to build?
```

**Design Review:**

```markdown
## Design Review: [Feature]

### Attendees
Product Trio

### Agenda

1. Context refresh (5 min)
   - Problem we're solving
   - Constraints reminder

2. Design walkthrough (20 min)
   - Walk through solution
   - Explain rationale
   - Show alternatives considered

3. Feedback (20 min)
   - Questions for clarification
   - Constructive critique
   - Engineering feasibility check

4. Next steps (5 min)
   - Changes to make
   - Timeline for next review
```

### Collaboration Patterns by Company Stage

| Stage | Team Structure | PM Focus |
|-------|---------------|----------|
| **Startup (< 10)** | Everyone does everything | Jack of all trades, ship fast |
| **Growth (10-50)** | Forming pods | Establish processes, hire |
| **Scale (50-200)** | Multiple pods | Cross-pod coordination |
| **Enterprise (200+)** | Platform + feature teams | Alignment, strategy |

### Anti-Patterns

- **Ticket tosser** — PM writes specs, throws over wall
- **Designer dictator** — PM makes UX decisions
- **Tech micromanager** — PM specifies implementation
- **Absent PM** — Never available for questions
- **Meeting multiplier** — Everything needs a meeting
- **Information hoarder** — Context stays with PM
- **Blame shifter** — Points fingers when things fail
- **Process zealot** — Process over outcomes
