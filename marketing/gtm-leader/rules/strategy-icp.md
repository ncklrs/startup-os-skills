---
title: Defining Your ICP
impact: CRITICAL
tags: strategy, icp, targeting, segmentation
---

## Defining Your ICP

**Impact: CRITICAL**

ICP (Ideal Customer Profile) is the specific type of customer where you win the most and churn the least. Get this wrong and you'll spend money acquiring customers who leave.

### ICP vs Persona vs TAM

| Concept | What It Is | Example |
|---------|------------|---------|
| **TAM** | Everyone who could theoretically buy | All companies with developers |
| **ICP** | Companies where you consistently win | Series A-C startups, 20-200 employees, using cloud infrastructure |
| **Persona** | Individual decision-maker/user | Senior DevOps engineer, 5+ years experience |

### ICP Framework

**Firmographics (Company)**
- Company size (employees, revenue)
- Industry/vertical
- Technology stack
- Funding stage
- Geography

**Situation**
- Pain trigger (what happened to make them look?)
- Current solution (what are they using now?)
- Budget availability
- Decision timeline

**Behavior**
- How they buy (self-serve vs sales-assisted)
- Where they research (Google, Twitter, communities)
- Who's involved in decision

### Building Your ICP

**Step 1: Analyze best customers**
Look at customers who:
- Converted fastest
- Pay the most
- Churn the least
- Refer others
- Expand over time

**Step 2: Find patterns**
```
What do your best 10 customers have in common?
- Company size: 50-200 employees
- Stage: Series A or B
- Tech stack: AWS, uses containers
- Trigger: Recent security incident or audit
- Buyer: Engineering leader
```

**Step 3: Validate with negatives**
Who are your worst customers?
- Churned within 6 months
- Constant support tickets
- Tried to negotiate heavily
- Never fully activated

**Step 4: Write it down**

```
ICP: SecretStash

Companies:
- SaaS/tech startups
- 20-200 employees
- Series A through C
- Using cloud infrastructure (AWS, GCP, Azure)
- Have at least 5 developers

Situation:
- Managing secrets in .env files or basic vault
- Recent security scare or upcoming compliance audit
- Moving fast, can't afford complex enterprise tools

Decision maker: Engineering Manager or CTO
User: Individual developers
Budget: $500-5,000/month
```

### Segmentation Strategy

**Beachhead → Expand**

```
Phase 1 (Beachhead):
Series A startups, 20-50 employees, dev tools space
→ Easiest to reach, fastest sales cycle, tolerant of early product

Phase 2 (Expand):
Series B-C startups, 50-200 employees, any tech vertical
→ Higher ACV, still PLG-friendly

Phase 3 (Scale):
Enterprise companies with modern dev teams
→ Requires sales team, longer cycles, higher ACV
```

### ICP Scoring

Rate each prospect on ICP fit:

| Signal | Strong Fit (+2) | Moderate (+1) | Weak (-1) |
|--------|-----------------|---------------|-----------|
| Size | 50-200 employees | 20-50 or 200-500 | <20 or >500 |
| Stage | Series A-C | Seed or Series D+ | Pre-seed or Public |
| Stack | Cloud-native | Hybrid | On-prem |
| Trigger | Active evaluation | Passive research | No trigger |

### Anti-Patterns

- **ICP too broad** — "Any company with developers" (that's everyone)
- **ICP too narrow** — "Fintech startups in Austin with 47 employees"
- **Ignoring churn data** — Optimizing for acquisition, not retention
- **Static ICP** — Never updating as you learn
