---
title: Sales Playbook Creation
impact: HIGH
tags: playbook, process, methodology, documentation
---

## Sales Playbook Creation

**Impact: HIGH**

A playbook codifies what your best sellers do so everyone can replicate success. Without it, you're scaling tribal knowledge.

### What Goes in a Sales Playbook

| Section | Purpose | Update Frequency |
|---------|---------|------------------|
| **ICP & Personas** | Who we sell to | Quarterly |
| **Value Proposition** | Why customers buy | Quarterly |
| **Sales Process** | How deals progress | Semi-annually |
| **Discovery Framework** | How to qualify | Semi-annually |
| **Demo Flow** | How to present | Quarterly |
| **Objection Handling** | How to respond | Monthly |
| **Competitive Intel** | How to position | Monthly |
| **Talk Tracks** | What to say | Quarterly |
| **Email Templates** | Outreach sequences | Monthly |
| **Case Studies** | Proof points | Quarterly |
| **Pricing Guidance** | How to quote | As needed |

### Good Playbook Structure

```markdown
# Enterprise Sales Playbook

## Quick Reference
- [30-Second Pitch](#30-second-pitch)
- [Discovery Questions](#discovery-questions)
- [Top Objections](#objection-handling)
- [Competitor Comparisons](#competitive-intel)

---

## 1. Who We Sell To

### Ideal Customer Profile
| Attribute | Ideal | Acceptable | Disqualify |
|-----------|-------|------------|------------|
| Company Size | 500-5000 emp | 200-500 emp | <100 emp |
| Industry | Tech, Finance, Healthcare | Manufacturing | Government |
| Tech Stack | AWS/GCP, Kubernetes | Azure | Legacy only |
| Growth | 30%+ YoY | 15-30% YoY | Declining |
| Budget Owner | VP+ Engineering | Director | Individual |

### Buyer Personas

**Primary: VP of Engineering**
- **Goals:** Ship faster, reduce outages, improve security posture
- **Pains:** Too many tools, alert fatigue, compliance burden
- **Triggers:** Security incident, audit failure, team scaling
- **Objections:** "We built something internally"
- **Wins With:** ROI data, peer references, security credentials

**Influencer: DevOps Lead**
- **Goals:** Simplify toolchain, automate everything, look good to boss
- **Pains:** Tool sprawl, manual processes, on-call burden
- **Triggers:** New role, major incident, performance review
- **Objections:** "My team won't adopt another tool"
- **Wins With:** Technical depth, integration ease, community

---

## 2. Sales Process

### Stage Definitions

| Stage | Exit Criteria | Probability | Avg Duration |
|-------|---------------|-------------|--------------|
| **Discovery** | MEDDIC qualified, pain confirmed | 20% | 7 days |
| **Evaluation** | Technical win, security approved | 40% | 21 days |
| **Proposal** | Proposal delivered, budget confirmed | 60% | 14 days |
| **Negotiation** | Terms agreed, legal complete | 80% | 14 days |
| **Closed Won** | Contract signed | 100% | — |

### Required Activities by Stage

**Discovery → Evaluation:**
☐ Discovery call completed (recorded)
☐ MEDDIC fields populated
☐ Pain statement documented
☐ Next steps confirmed with all stakeholders

**Evaluation → Proposal:**
☐ Technical evaluation completed
☐ Security questionnaire submitted
☐ Champion confirmed
☐ Economic buyer identified
☐ Decision criteria documented

---

## 3. Discovery Framework

### MEDDIC Checklist

| Element | Questions | Red Flags |
|---------|-----------|-----------|
| **Metrics** | "What KPIs are you measured on?" "How much is this problem costing you?" | Can't quantify impact |
| **Economic Buyer** | "Who signs off on purchases of this size?" "Have you worked with them before?" | Don't know, can't access |
| **Decision Criteria** | "What factors will drive your decision?" "How will you evaluate vendors?" | No defined criteria |
| **Decision Process** | "Walk me through how you've made similar decisions" "What's the approval process?" | Unknown, lengthy |
| **Identify Pain** | "Tell me about a time this problem caused issues" "What happens if you don't solve this?" | Nice-to-have, not urgent |
| **Champion** | "Who internally is pushing for this change?" "What's their stake?" | No internal advocate |

### Discovery Call Structure

```
OPENING (5 min)
- Thank them for time
- Confirm agenda and time
- Get permission to ask questions

CURRENT STATE (10 min)
- "Walk me through your current process for..."
- "How does your team handle X today?"
- "What tools are you using?"

PAIN EXPLORATION (15 min)
- "What's working well?"
- "Where do you see gaps?"
- "Can you give me an example of when that caused problems?"
- "What was the impact?"
- "How often does that happen?"

FUTURE STATE (10 min)
- "In an ideal world, what would this look like?"
- "What would success look like in 6 months?"
- "How would you measure that?"

MEDDIC QUALIFICATION (10 min)
- Decision process
- Timeline and urgency
- Stakeholders
- Budget

CLOSE (5 min)
- Summarize what you heard
- Confirm next steps
- Schedule follow-up
```

---

## 4. Objection Handling

### Top 5 Objections

**"We're happy with our current solution"**

ACKNOWLEDGE: "That's great to hear. Stability is important."
PROBE: "What do you like most about it? Are there areas where it falls short?"
REFRAME: "Many of our customers were satisfied too until [trigger event]. They found that [specific value prop] helped them [outcome]."
EVIDENCE: "Company X was in a similar situation and saw [result]."

**"It's too expensive"**

ACKNOWLEDGE: "I understand budget is always a consideration."
PROBE: "When you say too expensive, compared to what? What were you expecting?"
REFRAME: "Let's look at the total cost of the problem you're solving. You mentioned [pain] costs you [amount]. Our solution typically delivers [ROI] within [timeframe]."
EVIDENCE: "Here's how [customer] calculated their ROI..."

**"We'll build it ourselves"**

ACKNOWLEDGE: "Your team is clearly talented."
PROBE: "What would it take to build and maintain? What's the opportunity cost?"
REFRAME: "We've seen teams spend [X months] building 20% of what we offer. That's engineering time not spent on [their core product]."
EVIDENCE: "[Customer] started building internally, then switched to us. Here's why..."

---

## 5. Competitive Intel

### vs. Competitor A

| Category | Us | Competitor A |
|----------|-----|--------------|
| **Strength** | Enterprise security, SOC 2 | Lower price point |
| **Weakness** | Higher price | Limited integrations |
| **When We Win** | Security-conscious, complex environments | — |
| **When We Lose** | Price-sensitive, simple use case | — |

**Landmines to Plant:**
- "When you're evaluating solutions, make sure to ask about [capability they lack]"
- "Some vendors struggle with [our strength]. It's worth testing."

**Counter Their Claims:**
- They say: "We're more affordable"
- We say: "Total cost includes implementation, maintenance, and incidents. Let's compare TCO."
```

### Bad Playbook Example

```markdown
# Sales Playbook (Don't Do This)

## About Our Company
[3 pages of company history no one reads]

## Our Product
[Product documentation copy-pasted]

## How to Sell
- Do good discovery
- Build relationships
- Handle objections
- Close deals

## Objections
Q: Too expensive
A: Explain the value

Q: Happy with current solution
A: Show them why we're better

---

PROBLEMS:
✗ No specific guidance or examples
✗ Too theoretical, not actionable
✗ Generic advice anyone could write
✗ No talk tracks or scripts
✗ No competitive specifics
✗ Hasn't been updated in 18 months
```

### Playbook Adoption Strategies

| Strategy | Description | Impact |
|----------|-------------|--------|
| **Integrate with CRM** | Surface playbook content in deal context | High |
| **Manager reinforcement** | Managers reference in coaching | High |
| **Certification** | Test knowledge of playbook | Medium |
| **Gamification** | Reward usage and contributions | Medium |
| **Real examples** | Use actual calls and deals | High |
| **Keep it fresh** | Update monthly with new intel | Critical |

### Playbook Maintenance Schedule

| Content Type | Review Frequency | Owner |
|--------------|------------------|-------|
| ICP/Personas | Quarterly | Product Marketing |
| Competitive Intel | Monthly | Competitive Intel |
| Objection Handling | Monthly | Enablement |
| Talk Tracks | Quarterly | Enablement |
| Email Templates | Monthly | Sales Ops |
| Case Studies | Quarterly | Marketing |
| Pricing | As needed | RevOps |

### Anti-Patterns

- **Playbook as PDF** — Static document no one references
- **Written by marketing** — Sounds good, doesn't work in practice
- **No seller input** — Top performers not consulted
- **Too long** — 100 pages no one reads
- **Never updated** — Outdated competitive info, old pricing
- **Can't find anything** — Poor organization, no search
- **Theory over practice** — Concepts without talk tracks
- **Not role-specific** — Same playbook for SDR and enterprise AE
