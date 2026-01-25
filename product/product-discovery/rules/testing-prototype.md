---
title: Prototype Testing
impact: HIGH
tags: testing, prototypes, validation, concepts
---

## Prototype Testing

**Impact: HIGH**

Test concepts before building. A day of prototype testing saves months of building the wrong thing.

### Prototype Fidelity Spectrum

| Fidelity | What It Is | When to Use | Effort |
|----------|------------|-------------|--------|
| **Paper sketches** | Hand-drawn screens | Early exploration | Minutes |
| **Wireframes** | Low-fi digital layouts | Flow validation | Hours |
| **Clickable prototype** | Interactive but no real data | UX testing | Days |
| **High-fidelity prototype** | Looks real, fake backend | Concept validation | Days-Week |
| **Functional prototype** | Partial real functionality | Technical validation | Weeks |

### Choosing Prototype Fidelity

**Match Fidelity to Question**

```
QUESTION: "Is this the right problem to solve?"
→ Paper sketches, conversation
→ Don't need any prototype

QUESTION: "Does this workflow make sense?"
→ Low-fi wireframes, paper prototype
→ Test the flow, not the polish

QUESTION: "Can users complete this task?"
→ Clickable prototype
→ Enough to navigate, but not distracting

QUESTION: "Is this desirable/valuable?"
→ High-fidelity prototype
→ Must look real to get honest reaction

QUESTION: "Is this technically feasible?"
→ Functional prototype / spike
→ Real code, limited scope
```

### Paper Prototype Testing

**When to Use**
- Very early exploration
- Testing broad concepts
- Quick iteration needed
- Resource constraints

**How to Run**

```
SETUP:
1. Sketch key screens on paper/cards
2. Prepare a "starting screen"
3. Have blank cards ready for new screens

FACILITATION:
1. Explain: "This is an early idea, nothing is built yet"
2. Present starting screen
3. Ask: "What would you do to [accomplish task]?"
4. When they "click" — swap to next screen
5. Note confusion, hesitation, unexpected paths

DEBRIEF:
- What made sense?
- What was confusing?
- What's missing?
```

### Concept Testing

**Testing Ideas Before Execution**

| Method | What to Test | Artifacts Needed |
|--------|--------------|------------------|
| **Fake door** | Demand | Button/link that goes nowhere |
| **Landing page** | Value prop resonance | Single page, email capture |
| **Video demo** | Complex concept understanding | 60-90 second explainer |
| **Wizard of Oz** | End-to-end experience | Fake automation, real delivery |
| **Concierge** | Job-to-be-done | Manual service, learning |

**Concept Testing Script**

```
INTRO:
"I'm going to show you an early concept. It's not built yet —
we're trying to learn if it would be valuable."

FIRST IMPRESSION (before explaining):
"What do you think this is?"
"Who do you think it's for?"
"What do you expect it to do?"

WALKTHROUGH:
[Show concept]
"What stands out to you?"
"What questions do you have?"

VALUE ASSESSMENT:
"On a scale of 1-10, how valuable would this be to you?"
"What would make it more valuable?"
"What would you use instead if this didn't exist?"

PURCHASE INTENT:
"Would you pay for this?"
"What would you expect it to cost?"
"What would stop you from using this?"
```

### Clickable Prototype Testing

**Building the Prototype**

```
Tools: Figma, Sketch, InVision, Framer

Include:
- Happy path (main flow)
- Key decision points
- Error states (if testing robustness)
- Realistic content (not "Lorem ipsum")

Exclude:
- Every edge case
- Animations (unless testing animation)
- Complete design system
```

**Running the Test**

```
TASK-BASED TESTING:

1. Set context (but not instructions)
   "Imagine you're [scenario]. You want to [goal]."

2. Ask them to think aloud
   "Please tell me what you're thinking as you go."

3. Observe without helping
   Note: hesitations, wrong turns, questions

4. Ask follow-up questions
   "What did you expect to happen there?"
   "What would you do next?"

5. Debrief
   "How would you describe this to a colleague?"
   "What was confusing?"
   "What's missing?"
```

### Prototype Testing Metrics

**Measure During Testing**

| Metric | How to Capture | What It Tells You |
|--------|----------------|-------------------|
| **Task success** | Did they complete it? | Flow works/doesn't |
| **Time on task** | Stopwatch | Efficiency |
| **Error rate** | Count wrong paths | Clarity |
| **Hesitations** | Note pauses | Confusion points |
| **Help requests** | Count "how do I..." | Missing affordances |

**Measure After Testing**

| Metric | How to Ask | What It Tells You |
|--------|------------|-------------------|
| **Ease score** | "How easy? 1-7" | Perceived complexity |
| **Value score** | "How valuable? 1-10" | Desirability |
| **Likelihood to use** | "How likely? 1-10" | Intent |
| **Confidence** | "How confident were you?" | Clarity |

### A/B Prototype Testing

**Testing Multiple Concepts**

```
Approach 1: Within-subjects
- Show all concepts to each participant
- Randomize order
- Compare directly
- Good for: Understanding preferences

Approach 2: Between-subjects
- Show one concept per participant
- Different people see different versions
- Compare across groups
- Good for: Unbiased reactions
```

**Comparison Framework**

```
For each concept, rate:
- Clarity (do they understand it?)
- Value (do they want it?)
- Usability (can they use it?)
- Preference (which do they prefer?)

Then ask:
- "Which would you choose? Why?"
- "What would make [less preferred] better?"
```

### Common Prototype Testing Mistakes

**Mistake 1: Testing Too Early**
```
Problem: Concept is half-baked, feedback is noise
Fix: Know your key assumptions before testing
```

**Mistake 2: Testing Too Late**
```
Problem: Already committed, testing is theater
Fix: Test when you can still change direction
```

**Mistake 3: Testing with Wrong People**
```
Problem: Friends/colleagues aren't your users
Fix: Recruit actual target users
```

**Mistake 4: Explaining Too Much**
```
Problem: "Here's how it works..." removes realistic context
Fix: Set context, then observe
```

**Mistake 5: Asking Leading Questions**
```
Problem: "Don't you think this is easy?"
Fix: "How would you describe the difficulty?"
```

### Interpreting Results

**Strong Positive Signals**
```
+ Completed task without help
+ "When can I use this?"
+ Offered to pay / be design partner
+ Compared favorably to current solution
+ 8+ on value/likelihood scales
```

**Weak/Negative Signals**
```
- Needed explanation to proceed
- "This is interesting" (polite disinterest)
- "I could see using this" (hypothetical)
- Compared to competitors unfavorably
- < 6 on value/likelihood scales
```

**What to Do With Results**

| Finding | Action |
|---------|--------|
| Clear usability issues | Fix before building |
| Value unclear | Revisit positioning/messaging |
| Flow works, details wrong | Iterate design |
| Concept rejected | Revisit problem validation |
| Mixed signals | More testing needed |

### Rapid Iteration Cycles

**Test-Learn-Iterate Loop**

```
Day 1: Build prototype
Day 2: Test with 3 users
Day 3: Synthesize, identify top 3 issues
Day 4: Update prototype
Day 5: Test with 3 more users
...repeat until diminishing returns
```

**Iteration Decision Tree**

```
Did users complete the task?
├── Yes → Did they do it easily?
│         ├── Yes → Is the value clear?
│         │         ├── Yes → Ship it
│         │         └── No → Fix messaging
│         └── No → Fix usability issues
└── No → Is the concept right?
          ├── Yes → Fix critical blockers
          └── No → Revisit problem/concept
```

### Anti-Patterns

- **Pixel-perfect too early** — High-fi when you need to test concept, not polish
- **Testing in a vacuum** — No task context, just "what do you think?"
- **Helping too much** — Explaining when they struggle (they won't have you in real life)
- **Sample of one** — Major decisions from single test
- **Ignoring negative signals** — "They just didn't understand" (maybe it's unclear)
- **Feature validation theater** — Testing to confirm, not to learn
- **Prototype-production gap** — Prototype tests well, production doesn't match
