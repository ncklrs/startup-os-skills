---
title: Go-to-Market Coordination
impact: MEDIUM-HIGH
tags: gtm, launch, marketing, sales, coordination
---

## Go-to-Market Coordination

**Impact: MEDIUM-HIGH**

Great products fail without great go-to-market. PMs must bridge product development with how features reach customers.

### PM's Role in GTM

```
┌─────────────────────────────────────────────────────────────────┐
│                    PM GTM RESPONSIBILITIES                      │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│   PRODUCT SIDE                     GTM SIDE                     │
│   ────────────                     ────────                     │
│   • What we're building            • Why it matters to users    │
│   • When it ships                  • How to position it         │
│   • Technical capabilities         • Target segments            │
│   • Known limitations              • Success metrics            │
│                                                                 │
│                      PM BRIDGES BOTH                            │
│                     (translates and aligns)                     │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### GTM Planning by Launch Tier

| Tier | Criteria | GTM Investment | PM Involvement |
|------|----------|----------------|----------------|
| **Tier 1** | Major feature, new market, revenue impact | Full campaign | Heavy (lead) |
| **Tier 2** | Significant feature, existing market | Blog + email + enablement | Medium (coordinate) |
| **Tier 3** | Enhancement, iteration | Changelog + in-app | Light (inform) |
| **Tier 4** | Bug fix, minor improvement | Release notes only | Minimal |

### GTM Launch Checklist by Tier

**Tier 1 - Major Launch:**

```markdown
## Tier 1 GTM Checklist: [Feature Name]

### Positioning (PM + Marketing)
- [ ] Value proposition defined
- [ ] Target segments identified
- [ ] Competitive differentiation clear
- [ ] Messaging hierarchy approved

### Marketing Activities
- [ ] Launch blog post
- [ ] Email announcement (segmented)
- [ ] Social media campaign
- [ ] Press/analyst outreach
- [ ] Video/demo content
- [ ] Paid promotion (if applicable)

### Sales Enablement
- [ ] Sales deck updated
- [ ] Demo script created
- [ ] Competitive battle card
- [ ] FAQ document
- [ ] Training session completed
- [ ] Pricing/packaging confirmed

### Customer Success
- [ ] Existing customer communication
- [ ] Onboarding materials updated
- [ ] Success metrics defined
- [ ] Escalation path ready

### Product
- [ ] Help documentation
- [ ] In-app announcement
- [ ] Feature flags configured
- [ ] Analytics tracking live

### Timeline
| Milestone | Date | Owner |
|-----------|------|-------|
| Messaging approved | T-3w | Marketing |
| Sales training | T-2w | PM + Sales |
| Content ready | T-1w | Marketing |
| Launch | T | All |
```

**Tier 2/3 - Standard Launch:**

```markdown
## Tier 2/3 GTM Checklist: [Feature Name]

### Required
- [ ] Changelog entry
- [ ] Help docs updated
- [ ] In-app notification (if applicable)
- [ ] Support team informed

### Optional (Tier 2 only)
- [ ] Blog post
- [ ] Email to relevant segment
- [ ] Sales enablement brief
```

### Launch Brief Template

```markdown
## Launch Brief: [Feature Name]

### Overview
| Field | Detail |
|-------|--------|
| Launch Date | [Date] |
| Launch Tier | [1/2/3/4] |
| PM Owner | [Name] |
| Marketing Owner | [Name] |

### What We're Launching
[2-3 sentences describing the feature]

### Why It Matters
**For users:** [Problem solved, value delivered]
**For business:** [Revenue, retention, expansion impact]

### Target Audience
**Primary:** [Segment, persona]
**Secondary:** [Segment, persona]

### Key Messages
1. [Main message/headline]
2. [Supporting point 1]
3. [Supporting point 2]

### Competitive Context
[How this positions us vs competitors]

### Limitations / What This Isn't
- [Known limitation 1]
- [Known limitation 2]
- [What we're NOT launching yet]

### Success Metrics
| Metric | Target | Timeframe |
|--------|--------|-----------|
| [Metric 1] | [Target] | 30 days |
| [Metric 2] | [Target] | 90 days |

### Resources
- Product spec: [link]
- Design files: [link]
- Demo recording: [link]
- Help docs: [link]
```

### Coordinating with Marketing

| Marketing Needs | PM Provides |
|-----------------|-------------|
| **Launch timing** | Ship date, confidence level |
| **Key messages** | Value prop, user problems solved |
| **Target audience** | Who benefits most, segments |
| **Proof points** | Beta results, customer quotes |
| **Competitive positioning** | How we're different/better |
| **Limitations** | What to avoid claiming |
| **Demo content** | Walkthrough, screenshots |

**Timing alignment:**

```
Product Development          Marketing Prep
─────────────────────        ──────────────

Feature defined ─────────────► Start messaging work

Development start ───────────► Content planning

Beta launch ─────────────────► Draft content, collect feedback

Code complete ───────────────► Finalize content, prep campaigns

Ship ────────────────────────► Launch campaigns
```

### Coordinating with Sales

| Sales Needs | PM Provides |
|-------------|-------------|
| **Timeline** | When to start selling |
| **Pricing** | How it's priced/packaged |
| **Competitive** | Battle cards, differentiation |
| **Demo** | Script, environment |
| **Objection handling** | Common concerns + responses |
| **Customer stories** | Beta success, use cases |

**Sales enablement session agenda:**

```markdown
## Sales Enablement: [Feature Name]

### Agenda (45 min)

1. Overview (10 min)
   - What we built
   - Why it matters
   - Who it's for

2. Demo (15 min)
   - Live walkthrough
   - Key workflows
   - Wow moments

3. Selling guide (10 min)
   - Ideal customer profile
   - Discovery questions
   - Competitive positioning
   - Pricing and packaging

4. Q&A (10 min)
   - Open questions
   - Objection handling
   - Edge cases
```

### Customer Communication Hierarchy

| Audience | Communication Method | Timing |
|----------|---------------------|--------|
| **Beta customers** | Personal email from PM | Before launch |
| **Power users** | Segment email + in-app | Launch day |
| **All users** | In-app announcement | Launch day |
| **Prospects** | Marketing campaigns | Launch day+ |
| **Industry/press** | PR outreach | Launch day |

### Handling Launch Delays

```markdown
## Launch Delay Communication

### Internal (to stakeholders)

Subject: [Feature] launch moving to [New Date]

**What changed:** [Brief explanation]

**Impact:**
- Marketing: [Adjust campaign dates]
- Sales: [Update customer expectations]
- Support: [Shift training]

**New timeline:** [Date]

**What we need:** [Any decisions or actions]

---

### External (if promised to customers)

Subject: Update on [Feature]

We wanted to let you know that [Feature] will launch on
[New Date] instead of [Original Date].

We made this decision to [brief reason that benefits them].

In the meantime, here's what you can do: [workaround or interim solution]

Thank you for your patience. We're excited to deliver this
to you soon.
```

### Post-Launch GTM Activities

| Timeframe | Activity | Owner |
|-----------|----------|-------|
| **Day 1** | Monitor support tickets | PM + Support |
| **Week 1** | Collect early feedback | PM |
| **Week 2** | Share initial metrics | PM + Marketing |
| **Month 1** | Case study candidates | CS + Marketing |
| **Month 2** | Full metrics review | PM |
| **Quarter** | Iterate based on learnings | PM |

### Anti-Patterns

- **Ship and forget** — Launching without GTM plan
- **Marketing surprise** — "Oh, we're launching tomorrow?"
- **Over-promising** — Marketing claims beyond capability
- **Under-communicating** — Internal teams learn from customers
- **One-size-fits-all** — Same GTM for every feature
- **PM as marketer** — Writing all the copy yourself
- **Sales blindside** — Customers know before sales team
- **No feedback loop** — Not measuring GTM effectiveness
