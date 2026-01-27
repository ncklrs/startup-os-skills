---
title: Handling Technical Questions During Demos
impact: HIGH
tags: technique, questions, technical, responses
---

## Handling Technical Questions During Demos

**Impact: HIGH**

Technical questions during demos can either derail your narrative or strengthen your credibility. The key is knowing when to answer, when to defer, and how to do both gracefully.

### The Question Triage Matrix

| Question Type | Answer Now | Defer | Example |
|---------------|-----------|-------|---------|
| **Clarifying** | Yes | - | "Can you show that again?" |
| **Expanding** | Yes | - | "Does it also work with X?" |
| **Technical Simple** | Yes | - | "What browsers do you support?" |
| **Technical Deep** | - | Yes | "Walk me through your encryption at rest" |
| **Off-Topic** | - | Yes | "What's your mobile app roadmap?" |
| **Objection Disguised** | Maybe | Maybe | "How does this compare to X?" |

### The Three Response Modes

**Mode 1: Answer Now**
```
When:  Question is quick, relevant, strengthens narrative

"Great question. Yes, we support [X]. In fact, let me
show you that quickly... [10-second demo]. Now, back
to [current topic]..."
```

**Mode 2: Defer Gracefully**
```
When:  Answer would take >2 minutes or derail the demo

"That's an important question and I want to give it
proper attention. Let me note that down [write it down
visibly] and we can either dig into it at the end or
schedule a technical deep-dive with our solutions team.
Does that work?"
```

**Mode 3: Bridge and Redirect**
```
When:  Question is related but better answered in context

"That's actually a perfect lead-in to what I'm about
to show you. Hold that thought for about 2 minutes,
and I think I'll answer it better with a live example."
```

### Question Categories and Responses

**Security Questions:**

| Question | Quick Answer | Promise for Deep-Dive |
|----------|--------------|----------------------|
| "Is it SOC 2 compliant?" | "Yes, Type II. I can share our report." | Security documentation package |
| "Where is data stored?" | "AWS US-East, with options for EU." | Architecture review call |
| "How do you handle SSO?" | "We support SAML, OIDC, and specific providers." | IT integration call |
| "What about encryption?" | "256-bit at rest and in transit." | Security deep-dive |

**Integration Questions:**

| Question | Quick Answer | Promise for Deep-Dive |
|----------|--------------|----------------------|
| "Does it integrate with X?" | "Yes/No/Via Zapier" | Integration options doc |
| "What's your API like?" | "RESTful, well-documented, rate-limited" | API documentation |
| "Can we do custom integrations?" | "Yes, via API or custom development" | Technical scoping call |
| "What about data import?" | "CSV, API, or we can help migrate" | Implementation planning |

**Performance Questions:**

| Question | Quick Answer | Promise for Deep-Dive |
|----------|--------------|----------------------|
| "How fast is it?" | "Typical page loads under 2 seconds" | Performance benchmarks |
| "What's your uptime?" | "99.9% SLA, historically 99.97%" | SLA documentation |
| "Can it handle our scale?" | "We handle [X customers doing Y]" | Scale assessment |
| "What about concurrent users?" | "No limit, built for enterprise" | Architecture review |

### The "I Don't Know" Script

**When you genuinely don't know:**

```
"That's a great question, and I want to give you an
accurate answer rather than guess. Let me write that
down and get you a precise response by [specific time].
Is that okay?"
```

**Never:**
- Make up an answer
- Say "I think so"
- Promise features you can't confirm
- Pretend you didn't hear

### Managing the Question Dominator

**When one person asks 80% of questions:**

```
Strategy 1: Acknowledge and broaden
"Great questions, [Name]. Let me also check in with
the rest of the group — any questions from others
before we move on?"

Strategy 2: Validate and defer
"[Name], you clearly have a strong technical background.
I'd love to set up a dedicated session with our solutions
architect to go deep on these. For now, let me make sure
we cover the core use cases for the whole team."

Strategy 3: Answer then redirect
"Good question. [Quick answer]. Now, [Other person],
does that address the concern you mentioned earlier
about [topic]?"
```

### Turning Questions into Opportunities

**Question as proof point:**
```
Q: "Can it handle complex approval workflows?"
A: "Absolutely. In fact, let me show you exactly that.
   This is a workflow [Similar Company] built that has
   seven approval stages across three departments..."
```

**Question as discovery:**
```
Q: "Does it integrate with [specific tool]?"
A: "Yes. Actually, I'm curious — how central is [tool]
   to your workflow? Understanding that helps me show
   you the right integration depth."
```

**Question as commitment:**
```
Q: "What kind of training do you offer?"
A: "We have comprehensive onboarding. If training is
   important — and I'm guessing it is given your team
   size — would that be something you'd want included
   in the proposal?"
```

### The Parking Lot Method

**Visual parking lot for remote demos:**

```
Share a note or slide with:

┌──────────────────────────────────────────────┐
│ PARKING LOT - Questions for Follow-up        │
├──────────────────────────────────────────────┤
│ 1. SSO integration specifics - [Name]        │
│ 2. API rate limits - [Name]                  │
│ 3. Custom field options - [Name]             │
└──────────────────────────────────────────────┘

"I'm putting this in our parking lot so we don't
lose it. We'll come back to it at the end."
```

**End of demo parking lot review:**
```
"Let me quickly go through our parking lot.
[Question 1] — [Brief answer or commit to follow up]
[Question 2] — [Brief answer or commit to follow up]
Any of these need more time today, or should I follow
up via email with the details?"
```

### Handling "Gotcha" Questions

**Signs of a gotcha:**
- Asked in front of group
- About known weakness
- Competitor-planted question
- Designed to embarrass

**Response framework:**
```
1. Stay calm (don't get defensive)
2. Acknowledge the valid concern
3. Provide honest context
4. Pivot to strength

Example:
Q: "I heard your mobile app is basically unusable."

A: "Mobile has been a focus area for us. Earlier this
   year, we completely rebuilt the app, and the reviews
   have jumped from 2.5 to 4.5 stars. I'd be happy to
   show you the current experience if mobile is
   important to your team — is it?"
```

### Question Response Templates

**For feature confirmation:**
```
"Yes, we do that. Would you like to see it now, or
should I note it for later?"
```

**For feature gap:**
```
"We don't have that today. [Alternative approach] is
how our customers typically handle that. Would that
work for your use case?"
```

**For roadmap items:**
```
"That's on our roadmap for [timeframe]. I can't make
promises, but I can connect you with our product team
if it's critical for your decision."
```

**For pricing:**
```
"Pricing depends on [factors]. Let me make sure we
scope your needs correctly first, and I'll have
[AE Name] put together a specific proposal."
```

### Anti-Patterns

- **Answering before they finish** — Interrupting the question
- **Over-answering** — 5-minute response to simple question
- **Getting defensive** — Taking questions as attacks
- **Faking knowledge** — Guessing or making things up
- **Never deferring** — Trying to answer everything
- **Losing control** — Demo becomes Q&A session
- **Forgetting parking lot** — Not following up on deferred questions
- **One-word answers** — "Yes." with no context
