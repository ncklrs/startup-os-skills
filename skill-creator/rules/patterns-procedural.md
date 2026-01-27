---
title: Procedural Skill Pattern
impact: MEDIUM
tags: patterns, skill-types
---

## Procedural Skill Pattern

**Impact: MEDIUM**

For encoding step-by-step workflows and processes.

### When to Use

- Multi-step procedures
- Checklists and runbooks
- Decision trees
- Operational playbooks

### Structure

Single SKILL.md with numbered steps and decision points.

### Example Format

```markdown
---
name: incident-response
description: Incident response playbook for production issues.
             Use when handling outages, security incidents, or
             critical bugs in production.
---

# Incident Response

## Triage (First 5 Minutes)

1. **Assess severity**
   - P1: Customer-facing, revenue impact
   - P2: Degraded but functional
   - P3: Internal, non-urgent

2. **Notify stakeholders**
   - P1: Page on-call, notify leadership
   - P2: Slack alert to team
   - P3: Create ticket

3. **Start incident channel**
   - Create #incident-YYYY-MM-DD-description
   - Post initial assessment

## Investigation

4. **Check dashboards**
   - [ ] Error rates
   - [ ] Latency percentiles
   - [ ] Resource utilization

5. **Review recent changes**
   - [ ] Deployments in last 24h
   - [ ] Config changes
   - [ ] Infrastructure changes

## Resolution

6. **Implement fix or rollback**
7. **Verify recovery**
8. **Update status page**
9. **Schedule post-mortem**
```

### What Makes It Work

- **Numbered steps** — Clear sequence
- **Checklists** — Nothing gets missed
- **Decision points** — Handle branching logic
- **Time anchors** — "First 5 minutes", "Within 1 hour"

### Anti-Pattern

Don't write procedures as prose. Use numbered steps and checklists for clarity.
