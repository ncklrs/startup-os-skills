---
title: Problem Discovery & Validation
impact: CRITICAL
tags: discovery, validation, problems, product-market-fit
---

## Problem Discovery & Validation

**Impact: CRITICAL**

The most expensive mistake in product is building something no one needs. Problem validation prevents building solutions to non-problems.

### Problem vs Solution Fit

```
┌─────────────────────────────────────────────────────────┐
│                    PRODUCT SUCCESS                      │
│                                                         │
│   Problem-Solution Fit    →    Product-Market Fit       │
│   (Are we solving a         (Can we scale this         │
│    real problem?)            profitably?)              │
│                                                         │
│   Discovery Phase          →    Growth Phase            │
└─────────────────────────────────────────────────────────┘

Most startups fail at Problem-Solution Fit.
They build solutions to problems that:
- Don't exist
- Aren't painful enough
- Affect too few people
- People won't pay to solve
```

### Problem Validation Framework

**The 4 U's of Problem Validation**

| Criteria | Question | Validation Method |
|----------|----------|-------------------|
| **Unworkable** | Is the current situation truly broken? | Interview: "What happens if this isn't solved?" |
| **Unavoidable** | Can they work around it? | Interview: "How do you handle this today?" |
| **Urgent** | Is it a priority right now? | Interview: "Where does this rank vs other priorities?" |
| **Underserved** | Are existing solutions inadequate? | Interview: "What have you tried? What's missing?" |

**Scoring:**
- 4/4 U's = Validated problem worth solving
- 3/4 U's = Promising, investigate further
- 2/4 U's = Weak problem, likely won't sustain business
- 1/4 U's = Not a real problem

### Problem Interview Script

**Setup (2 min)**
```
"Thanks for talking with me. I'm trying to understand how
people handle [problem area]. There are no right or wrong
answers — I'm here to learn from your experience."
```

**Current State (10 min)**
```
"Tell me about your role and what you're responsible for."
"Walk me through how you currently handle [area]."
"What tools or processes do you use?"
"How much time do you spend on this each week?"
```

**Problem Exploration (15 min)**
```
"What's the hardest part about [area]?"
"Tell me about the last time that happened."
"What did you do? How did it turn out?"
"How often does this happen?"
"On a scale of 1-10, how painful is this? Why that number?"
```

**Attempted Solutions (10 min)**
```
"What have you tried to solve this?"
"How well did that work? What's still missing?"
"Have you looked at other solutions? Which ones?"
"Why haven't you solved this yet?"
```

**Prioritization (5 min)**
```
"If you could wave a magic wand, what would change?"
"Where does solving this rank among your priorities?"
"What would happen if this never got solved?"
"Is this something your company would pay to solve?"
```

### Validation Signals

**Strong Problem Signals**
```
+ They've already tried to solve it (spent money/time)
+ They describe specific negative consequences
+ They can quantify the cost (time, money, opportunity)
+ Multiple people independently mention same problem
+ They ask when your solution will be ready
+ They offer to pay or be a design partner
```

**Weak Problem Signals**
```
- "That would be nice to have"
- "I could see using that"
- Can't give specific examples
- Haven't tried to solve it themselves
- Problem is theoretical, not experienced
- Only one person mentions it
```

**Danger Signals**
```
! They're being polite, not honest
! They want to help you, not themselves
! "Yes, but..." followed by objections
! Can't describe current workaround
! Would use if free, but wouldn't pay
```

### Problem Stack Ranking

**Create a Problem Stack from Interviews**

| Problem | Frequency | Severity | Existing Solutions | Score |
|---------|-----------|----------|-------------------|-------|
| Manual data entry | 8/10 mention | 8/10 pain | Excel, hacky scripts | 24 |
| Report generation | 6/10 mention | 7/10 pain | Manual, basic tools | 19 |
| Data accuracy | 5/10 mention | 9/10 pain | Double-checking | 18 |
| Collaboration | 4/10 mention | 5/10 pain | Email, Slack | 11 |

**Scoring Formula:**
```
Problem Score = (Frequency × 3) + (Severity × 2) + (Solution Gap × 1)

Where:
- Frequency = How many interviewees mentioned (1-10)
- Severity = How painful when it occurs (1-10)
- Solution Gap = How inadequate current solutions are (1-10)
```

### Problem Statement Templates

**Format 1: Situation-Complication-Question**
```
Situation: [Current state]
Complication: [What makes it problematic]
Question: [What needs to be solved]

Example:
Situation: Engineering teams manage secrets across multiple environments.
Complication: Secrets are scattered in .env files, Slack messages, and wikis,
             leading to security risks and onboarding delays.
Question: How might we give teams a secure, centralized way to manage secrets
          that's as easy as copy-paste?
```

**Format 2: User-Problem-Impact**
```
[User segment] struggle with [problem]
which causes [negative impact].

Example:
DevOps engineers at startups struggle with secret sprawl
which causes security vulnerabilities and slows down new hire onboarding by 2+ days.
```

**Format 3: Job-to-be-Done**
```
When [situation], I want to [motivation],
so I can [expected outcome].

Example:
When onboarding a new developer, I want to give them access to all necessary secrets,
so I can get them productive on day one without compromising security.
```

### Validation Experiments

**Before Building Anything**

| Experiment | Effort | Signal Strength | When to Use |
|------------|--------|-----------------|-------------|
| **Problem interviews** | Low | High | Always first |
| **Landing page test** | Low | Medium | Validate demand |
| **Concierge MVP** | Medium | High | Test workflow manually |
| **Wizard of Oz** | Medium | High | Fake automation, real value |
| **Smoke test** | Low | Medium | Measure intent to purchase |

**Landing Page Test**
```
Create a page describing the problem and solution.
Add an email capture: "Get early access"
Drive traffic (ads, posts, outreach)

Success metrics:
- > 20% email signup rate = strong signal
- 10-20% = promising
- < 10% = weak problem or messaging
```

**Smoke Test**
```
Describe the solution with pricing.
Add "Buy Now" or "Start Trial" button.
Capture clicks (no actual purchase).

Success metrics:
- > 5% click = strong buying intent
- 2-5% = worth exploring
- < 2% = problem or pricing issue
```

### Problem Pivot Signals

**When to Pivot Your Problem Focus**
```
- 5+ interviews with no consistent pain points
- Users satisfied with existing solutions
- Problem exists but won't pay to solve
- Market too small (< $10M opportunity)
- Problem is symptom, not root cause
```

**Adjacent Problem Exploration**
```
Original problem: "Reports take too long"
Adjacent problems:
- Data is inaccurate
- Stakeholders don't read reports
- Insights aren't actionable
- Manual data collection

Sometimes the bigger problem is next door.
```

### Anti-Patterns

- **Solution-first thinking** — Starting with "what if we built X" instead of "what problem exists"
- **Proxy validation** — Asking friends/investors instead of target customers
- **Confirmation bias** — Only hearing problems that fit your solution
- **Single-interview decisions** — One person ≠ a market
- **Feature requests as problems** — "I want X" is not the same as "I struggle with Y"
- **Hypothetical validation** — "Would you use X?" vs "Tell me about last time..."
- **Ignoring workarounds** — If they've built workarounds, you've found a problem
