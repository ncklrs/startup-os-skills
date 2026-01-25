---
title: Stakeholder Mapping During Discovery
impact: HIGH
tags: discovery, stakeholders, multi-threading, buying-committee
---

## Stakeholder Mapping During Discovery

**Impact: HIGH**

Deals are won and lost based on stakeholder mapping. Single-threaded deals die. Multi-threaded deals close.

### The Buying Committee

```
┌─────────────────────────────────────────────────────────────────────┐
│                       BUYING COMMITTEE                               │
├─────────────────────────────────────────────────────────────────────┤
│                                                                      │
│                      ┌──────────────────┐                           │
│                      │  ECONOMIC BUYER  │                           │
│                      │  (Final sign-off) │                           │
│                      └────────┬─────────┘                           │
│                               │                                      │
│              ┌────────────────┼────────────────┐                    │
│              │                │                │                     │
│    ┌─────────▼──────┐  ┌──────▼──────┐  ┌─────▼─────────┐          │
│    │   CHAMPION     │  │  TECHNICAL   │  │   COACH       │          │
│    │ (Sells for you)│  │  EVALUATOR   │  │(Inside intel) │          │
│    └────────────────┘  └─────────────┘  └───────────────┘          │
│                               │                                      │
│                      ┌────────▼────────┐                            │
│                      │    END USERS    │                            │
│                      │  (Adopt or reject)│                           │
│                      └─────────────────┘                            │
│                                                                      │
│    ┌─────────────────┐                                              │
│    │    BLOCKER      │ ← May appear at any level                    │
│    │(Has objections) │                                              │
│    └─────────────────┘                                              │
│                                                                      │
└─────────────────────────────────────────────────────────────────────┘
```

### Stakeholder Roles Explained

| Role | Definition | What They Care About | How to Engage |
|------|------------|---------------------|---------------|
| **Economic Buyer** | Signs the check, final authority | ROI, business impact, risk | Executive briefing, business case |
| **Champion** | Internal advocate, sells for you | Solving their problem, looking good | Enable with content, mutual plan |
| **Technical Evaluator** | Assesses fit and feasibility | Features, integration, security | Deep dives, POC, documentation |
| **End Users** | Day-to-day operators | Ease of use, time savings | Demo, trial, references |
| **Coach** | Provides inside information | Helping you navigate | Relationship building |
| **Blocker** | Resists the purchase | Status quo, budget, competing priorities | Address concerns directly |

### Discovery Questions for Stakeholder Mapping

**Identifying the committee:**
```
"Walk me through how decisions like this typically get made at [Company]."

"Who else would need to be involved in evaluating a solution like this?"

"If you found something you loved, who would you need to get buy-in from?"

"Is there anyone who might have concerns about making a change here?"

"Who owns the budget for initiatives like this?"
```

**Understanding each stakeholder:**
```
"What does [Person] care most about when evaluating new tools?"

"How would [Person] define success for this project?"

"What objections might [Person] raise?"

"What would get [Person] excited about this?"
```

**Building multi-threading:**
```
"Would it make sense to include [Role] in our next conversation?"

"I'd love to understand [Technical Lead]'s requirements. Would you
be open to a brief call with them?"

"What would be helpful for you to share with [Economic Buyer]?"
```

### Stakeholder Mapping Template

```
STAKEHOLDER MAP: [Company Name]

ECONOMIC BUYER:
- Name: Sarah Chen
- Title: VP of Engineering
- Priority: ROI, risk reduction
- Status: Not yet engaged
- Next step: Request intro through champion

CHAMPION:
- Name: Mike Rodriguez
- Title: DevOps Lead
- Priority: Solving daily pain, looking competent
- Status: Actively engaged
- Next step: Arm with business case

TECHNICAL EVALUATOR:
- Name: TBD
- Title: Security Engineer
- Priority: Integration, compliance
- Status: Unknown
- Next step: Ask Mike for intro

END USERS:
- Team: Platform Engineering (8 people)
- Priority: Ease of use
- Status: Haven't met
- Next step: Include in demo

POTENTIAL BLOCKER:
- Name: Director of IT
- Title: Controls infrastructure budget
- Concern: "We already have Vault"
- Status: Unknown
- Next step: Understand relationship with DevOps

COACH:
- Name: Mike Rodriguez (also champion)
- Intel: Budget cycle is Q4, CTO makes final calls
```

### Multi-Threading Strategies

**The Meeting Expansion:**
```
After discovery with your contact:
"This was really helpful. Based on what you shared about [technical
requirements], would it make sense to have [Security Lead] join our
next call? I want to make sure we address their needs too."
```

**The Content Bridge:**
```
"I have a case study from [similar company] that I think would
resonate with your CFO. Would it be helpful if I sent that over
for you to share, or would you prefer I send it directly?"
```

**The Org Chart Request:**
```
"Help me understand the landscape. Beyond yourself, who else has
a stake in solving this problem? I want to make sure we're
addressing everyone's concerns."
```

### Champion Development

**What makes a strong champion:**
- Has authority/influence
- Has the problem you solve
- Is motivated to solve it now
- Will advocate internally
- Shares inside information

**How to build champions:**
```
1. Make them successful - solve their problem
2. Make them look good - arm them with content
3. Make them informed - share industry insights
4. Make them powerful - give them inside access
5. Make them confident - prepare them for objections
```

**Arming your champion:**
```
"Here's a one-pager you can share with your VP that summarizes
the business case."

"What objections do you expect from [Blocker]? Let me help you
prepare responses."

"Would it help if I drafted an email you could send to
[Economic Buyer]?"
```

### Identifying and Handling Blockers

**Common blockers:**

| Blocker Type | Their Concern | Strategy |
|--------------|---------------|----------|
| **Status Quo Defender** | "Current system works fine" | Quantify cost of status quo |
| **Budget Guardian** | "Too expensive" | Build ROI case |
| **Competing Priority** | "Other projects first" | Create urgency |
| **Prior Bad Experience** | "We tried this before" | Differentiate, address concerns |
| **Turf Protector** | "This is my domain" | Include them, give ownership |

**Questions to identify blockers:**
```
"Is there anyone who might be skeptical about making a change?"

"Who might see this as impacting their area of responsibility?"

"What pushback have you gotten when raising this internally before?"

"Is anyone invested in the current solution?"
```

### Stakeholder Coverage Goals

| Deal Size | Minimum Contacts | Ideal Coverage |
|-----------|------------------|----------------|
| <$10K ARR | 1-2 | Champion + 1 |
| $10-50K ARR | 2-3 | Champion + Tech + User |
| $50-100K ARR | 3-4 | Champion + Tech + Econ Buyer |
| >$100K ARR | 5+ | All roles covered |

### Warning Signs

| Signal | What It Means | Action |
|--------|---------------|--------|
| Can't identify economic buyer | May not be real opportunity | Ask directly, escalate |
| Single-threaded 3+ meetings | Risk of deal dying | Push for additional contacts |
| Champion avoiding introductions | May not be true champion | Test commitment |
| Stakeholders contradict each other | Misaligned priorities | Facilitate alignment |
| New stakeholder appears late | Governance/process issue | Start discovery with them |

### Anti-Patterns

- **Single-threading** — Only talking to one person throughout deal
- **Bypassing champion** — Going around your contact (damages trust)
- **Assuming org structure** — Every company is different
- **Ignoring end users** — They can tank adoption
- **Not identifying blockers** — They appear at worst times
- **No champion development** — Expecting them to sell for you naturally
