---
title: Usability Testing
impact: HIGH
tags: testing, usability, ux, validation
---

## Usability Testing

**Impact: HIGH**

Usability testing reveals whether real users can accomplish real tasks with your product. It's the fastest way to find friction before it costs you customers.

### Usability Testing Fundamentals

**What Usability Testing Measures**

| Dimension | Question | How to Measure |
|-----------|----------|----------------|
| **Effectiveness** | Can they complete the task? | Success rate |
| **Efficiency** | How long does it take? | Time on task |
| **Learnability** | How easy to learn? | First vs repeat performance |
| **Error tolerance** | Can they recover from mistakes? | Error rate, recovery rate |
| **Satisfaction** | How do they feel about it? | Post-task ratings |

### When to Run Usability Tests

**Appropriate for Usability Testing**
```
- Evaluating existing product flows
- Testing redesigned features
- Comparing design alternatives
- Finding friction in onboarding
- Validating information architecture
- Testing with specific user segments
```

**Not Appropriate for Usability Testing**
```
- Validating if problem is worth solving (use problem interviews)
- Predicting market adoption (use concept testing)
- Understanding user needs (use discovery interviews)
- Measuring actual usage (use analytics)
```

### Test Types

| Type | Participants | Best For | Trade-offs |
|------|--------------|----------|------------|
| **Moderated remote** | 1-on-1, video call | Deep insights, follow-up | Time-intensive |
| **Unmoderated remote** | Solo, recorded | Scale, convenience | Less depth |
| **In-person** | Face-to-face | Complex tasks, observation | Logistics |
| **Guerrilla** | Intercept in public | Quick feedback | Less control |

### Planning the Study

**Define Test Scope**

```
1. What are we testing?
   [Specific feature/flow]

2. What questions do we need answered?
   - Can users find X?
   - Do users understand Y?
   - Where do users get stuck?

3. Who are we testing with?
   [Target user criteria]

4. What's the success criteria?
   - X% complete task successfully
   - Average time < Y minutes
   - SUS score > Z
```

**Sample Size Guidelines**

| Goal | Sample Size | Why |
|------|-------------|-----|
| Find major issues | 5 users | Catches ~85% of problems |
| Find most issues | 8-10 users | Catches ~95% of problems |
| Compare designs | 10-15 per design | Statistical confidence |
| Segment comparison | 5+ per segment | Meaningful differences |

### Writing Tasks

**Good Task Characteristics**

```
- Scenario-based (realistic context)
- Goal-focused (what, not how)
- No hints (don't give away the answer)
- Specific enough to measure
- Important to actual usage
```

**Good vs Bad Tasks**

| Bad Task | Why It's Bad | Good Task |
|----------|--------------|-----------|
| "Click on Settings" | Gives away answer | "Change your notification preferences" |
| "Create a report" | Too vague | "Create a report showing last month's sales by region" |
| "Test the dashboard" | Not actionable | "Find out which product sold the most last week" |
| "Use the search feature" | Not goal-based | "Find the order you placed last Tuesday" |

**Task Template**

```
SCENARIO:
[Context that makes the task realistic]

TASK:
[Clear goal without instructions]

SUCCESS CRITERIA:
[How you'll know if they succeeded]

Example:
SCENARIO: You just signed up for the service and want to
          add your team members so they can start using it.

TASK: Add a colleague named "Alex Smith" with the email
      alex@example.com to your team.

SUCCESS CRITERIA: User lands on team page with new member visible.
```

### Facilitating the Session

**Session Structure (60 min)**

```
0:00 - Welcome and setup (5 min)
       - Thank them, explain purpose
       - Get consent for recording
       - Explain think-aloud protocol

0:05 - Background questions (5 min)
       - Relevant experience
       - Current tools/processes
       - Familiarity with product

0:10 - Tasks (40 min)
       - 3-5 tasks
       - Think aloud throughout
       - Post-task questions after each

0:50 - Wrap-up (10 min)
       - Overall impressions
       - SUS or satisfaction scale
       - Any questions from them
```

**Facilitator Do's and Don'ts**

| Do | Don't |
|----|-------|
| Stay neutral | React positively/negatively |
| Let them struggle (briefly) | Jump in to help |
| Ask "what are you thinking?" | Ask "why did you do that?" (judgmental) |
| Note what you observe | Only note what they say |
| Follow up on interesting moments | Stick rigidly to script |
| Thank them for confusion | Apologize for issues |

**Useful Probes**

```
When they pause:
- "What are you thinking?"
- "What do you expect to happen?"

When they click something:
- "What made you choose that?"
- "What do you expect to see?"

When they seem stuck:
- "What would you do in real life?"
- "Is there anything you'd like to try?"

When they complete a task:
- "How did that go?"
- "How confident are you that worked?"
```

### Think-Aloud Protocol

**Concurrent Think-Aloud**
```
User narrates while doing.
+ Real-time insights
- Can affect behavior
- Some users struggle
```

**Retrospective Think-Aloud**
```
User watches their recording and narrates.
+ More natural behavior during test
- Slower, requires replay
- Some details forgotten
```

**Coaching Think-Aloud**
```
INTRODUCTION:
"As you go through the tasks, please tell me what you're
thinking out loud — what you're looking at, what you're
trying to do, what you expect to happen, any reactions you have.

Pretend you're alone working through this, but talking to yourself.
There are no wrong answers — we're testing the product, not you."

REMINDERS:
"What are you thinking right now?"
"Keep talking..."
```

### Measuring Results

**Quantitative Metrics**

| Metric | How to Calculate | Target |
|--------|------------------|--------|
| **Success rate** | % who completed task | >80% |
| **Time on task** | Average completion time | Context-dependent |
| **Error rate** | Errors per task | <1 per task |
| **Clicks to complete** | Average click count | Benchmark against optimal |
| **Task difficulty** | Post-task rating 1-7 | >5 average |

**System Usability Scale (SUS)**

```
10 questions, 1-5 scale (Strongly Disagree → Strongly Agree)

1. I would like to use this frequently
2. This is unnecessarily complex
3. This is easy to use
4. I would need support to use this
5. Functions are well integrated
6. Too much inconsistency
7. Most people would learn quickly
8. Very cumbersome to use
9. I felt confident using this
10. Needed to learn a lot before starting

Scoring:
- Odd questions: score - 1
- Even questions: 5 - score
- Sum × 2.5 = SUS score (0-100)

Interpretation:
- >80: Excellent
- 68-80: Good
- 50-67: Needs improvement
- <50: Poor
```

### Analyzing Findings

**Severity Rating Scale**

| Severity | Description | Action |
|----------|-------------|--------|
| **Critical (4)** | Prevents task completion | Must fix before launch |
| **Major (3)** | Causes significant delay/confusion | Fix soon |
| **Minor (2)** | Causes slight delay | Fix when possible |
| **Cosmetic (1)** | Noticed but doesn't affect task | Nice to fix |

**Findings Template**

```
FINDING: [Brief description]

SEVERITY: [1-4]

EVIDENCE:
- [X] of [Y] participants experienced this
- Task: [Which task]
- Behavior: [What happened]
- Quotes: "[What they said]"

RECOMMENDATION:
[Specific fix or direction to explore]
```

### Issue Prioritization Matrix

```
                    HIGH FREQUENCY
                          │
                          │
        CRITICAL FIXES    │    TOP PRIORITY
        (Many people,     │    (Many people,
         can work around) │     can't complete)
                          │
    ──────────────────────┼────────────────────
                          │
        LOW PRIORITY      │    FIX IF EASY
        (Few affected,    │    (Few people,
         minor impact)    │     big impact)
                          │
                    LOW FREQUENCY
```

### Remote Unmoderated Testing

**Tools:** UserTesting, Maze, Lookback, UsabilityHub

**When to Use:**
- Need more participants quickly
- Geographic diversity
- Limited budget for moderation
- Quantitative metrics priority

**Setup Checklist:**
```
[ ] Clear task instructions
[ ] Working prototype link
[ ] Screener questions
[ ] Recording consent
[ ] Post-task questions
[ ] Completion criteria
```

**Watch Out For:**
- Lower engagement than moderated
- Can't ask follow-up questions
- Technical issues with recording
- Participants may rush

### Reporting Results

**Usability Report Structure**

```
1. EXECUTIVE SUMMARY
   - Key findings (top 3-5)
   - Overall usability score
   - Recommended priorities

2. METHODOLOGY
   - Who we tested
   - What we tested
   - How we tested

3. FINDINGS BY TASK
   - Success rate
   - Time on task
   - Issues encountered
   - Severity ratings

4. TOP ISSUES
   - Issue description
   - Evidence
   - Severity
   - Recommendation

5. POSITIVE FINDINGS
   - What worked well
   - User quotes

6. RECOMMENDATIONS
   - Prioritized action items
   - Quick wins vs longer-term
```

### Anti-Patterns

- **Testing too late** — Product is built, can't change it
- **Testing with colleagues** — They're not your users
- **Too many tasks** — Participant fatigue, rushed responses
- **Leading participants** — "You'd click here, right?"
- **Helping too much** — Real users won't have you there
- **Ignoring positive signals** — Only focusing on problems
- **Death by metrics** — Measuring everything, learning nothing
- **Testing once** — Usability is iterative, not one-time
