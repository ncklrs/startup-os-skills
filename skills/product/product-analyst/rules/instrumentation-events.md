---
title: Data Instrumentation and Events
impact: HIGH
tags: instrumentation, events, tracking, data-quality
---

## Data Instrumentation and Events

**Impact: HIGH**

Bad data in, bad decisions out. Solid instrumentation is the foundation of all product analytics. Invest here first.

### Event Tracking Fundamentals

**What is an event?**
An event is a record of something that happened: a user action, system occurrence, or state change.

```
{
  "event": "button_clicked",
  "timestamp": "2024-01-15T10:30:00Z",
  "user_id": "user_123",
  "properties": {
    "button_name": "signup_cta",
    "page": "homepage",
    "variant": "blue"
  }
}
```

### Event Taxonomy Principles

**1. Naming Conventions**

| Convention | Format | Example |
|------------|--------|---------|
| **Object_Action** | noun_verb | signup_completed, project_created |
| **Action_Object** | verb_noun | completed_signup, created_project |
| **Page_Action** | context_verb | onboarding_step_viewed |

Pick ONE convention and stick to it.

**2. Event Hierarchy**

```
Level 1: Categories (high-level)
├── user_lifecycle
├── content_engagement
├── feature_usage
├── commerce
└── system

Level 2: Objects (what)
├── user_lifecycle
│   ├── signup
│   ├── login
│   └── subscription
├── feature_usage
│   ├── project
│   ├── report
│   └── export

Level 3: Actions (happened)
├── user_lifecycle
│   ├── signup
│   │   ├── started
│   │   ├── completed
│   │   └── failed
```

**3. Property Standards**

```
Every event should include:
┌─────────────────────────────────────────────────────────┐
│ Property        │ Type     │ Description               │
├─────────────────────────────────────────────────────────┤
│ timestamp       │ datetime │ When event occurred       │
│ user_id         │ string   │ Unique user identifier    │
│ session_id      │ string   │ Session identifier        │
│ platform        │ string   │ web, ios, android         │
│ app_version     │ string   │ Application version       │
└─────────────────────────────────────────────────────────┘

Event-specific properties:
┌─────────────────────────────────────────────────────────┐
│ Property        │ Type     │ Example                   │
├─────────────────────────────────────────────────────────┤
│ object_id       │ string   │ project_456               │
│ object_type     │ string   │ project                   │
│ value           │ number   │ 99.99                     │
│ source          │ string   │ email_campaign            │
│ variant         │ string   │ experiment_a              │
└─────────────────────────────────────────────────────────┘
```

### Building an Event Spec

**Event Specification Document:**

```
Event: project_created
Category: feature_usage
Description: User creates a new project

Trigger:
- When: After successful project save to database
- Where: Project creation flow (web, mobile)
- Who: Authenticated users only

Properties:
┌───────────────────────────────────────────────────────────────┐
│ Property       │ Type    │ Required │ Description            │
├───────────────────────────────────────────────────────────────┤
│ project_id     │ string  │ Yes      │ Unique project ID      │
│ project_name   │ string  │ Yes      │ User-defined name      │
│ template_used  │ string  │ No       │ Template ID if used    │
│ team_id        │ string  │ No       │ Team if shared         │
│ source         │ string  │ Yes      │ Where created from     │
│ time_to_create │ number  │ Yes      │ Seconds from start     │
└───────────────────────────────────────────────────────────────┘

Source values: onboarding, dashboard, import, api, template

Example:
{
  "event": "project_created",
  "timestamp": "2024-01-15T10:30:00Z",
  "user_id": "user_123",
  "properties": {
    "project_id": "proj_789",
    "project_name": "Q1 Marketing",
    "template_used": "marketing_template",
    "team_id": "team_456",
    "source": "template",
    "time_to_create": 45
  }
}
```

### Good vs Bad Event Design

**Good: Clear, Complete, Consistent**
```
// Clear event name
event: project_created

// Complete properties
properties: {
  project_id: "proj_123",
  project_type: "marketing",
  template_used: "q1_template",
  created_from: "dashboard",
  team_size: 5,
  is_first_project: true
}

// Consistent naming
- project_created (not "Created Project")
- project_updated (not "projectUpdated")
- project_deleted (not "delete_project")
```

**Bad: Vague, Incomplete, Inconsistent**
```
// Vague event name
event: click

// Missing context
properties: {
  button: "create"
}

// Inconsistent naming
- click
- Project Created
- updateProject
- deleted

Problems:
- Can't identify what was clicked
- Missing user context
- No way to build funnels
- Inconsistent casing
```

### Common Event Patterns

**1. Funnel Events**
```
signup_started        → Entry point
signup_email_entered  → Step 1
signup_password_set   → Step 2
signup_profile_done   → Step 3
signup_completed      → Success
signup_failed         → Track errors
```

**2. Feature Usage Events**
```
feature_viewed        → Saw the feature
feature_clicked       → Interacted
feature_used          → Completed action
feature_error         → Something went wrong
```

**3. Commerce Events**
```
product_viewed        → Browsing
product_added_to_cart → Intent
checkout_started      → High intent
purchase_completed    → Conversion
```

**4. Search/Discovery Events**
```
search_performed      → User searched
search_results_shown  → Results displayed
search_result_clicked → Selected result
search_no_results     → Empty state
```

### Data Quality Monitoring

**Quality Dimensions:**

| Dimension | What to Check | Alert Threshold |
|-----------|---------------|-----------------|
| **Completeness** | % of required properties filled | <95% |
| **Freshness** | Lag from event to warehouse | >15 minutes |
| **Volume** | Event count vs expected | ±30% from baseline |
| **Validity** | % passing schema validation | <99% |
| **Uniqueness** | Duplicate event rate | >1% |

**Monitoring Dashboard:**

```
Event Health Check (Last 24h):
┌────────────────────────────────────────────────────────────┐
│ Event              │ Count    │ Quality │ Status          │
├────────────────────────────────────────────────────────────┤
│ signup_completed   │ 2,450    │ 99.2%   │ ✓ Healthy       │
│ project_created    │ 8,230    │ 98.7%   │ ✓ Healthy       │
│ report_exported    │ 1,120    │ 87.3%   │ ⚠ Low quality   │
│ purchase_completed │ 342      │ 99.8%   │ ✓ Healthy       │
│ feature_x_used     │ 0        │ N/A     │ ✗ No events     │
└────────────────────────────────────────────────────────────┘

Alerts:
- report_exported: Missing 'format' property in 12% of events
- feature_x_used: No events in 24h (expected 500+)
```

### Implementation Best Practices

**1. Single Source of Truth**
```
Good:
- Event fired from one location in code
- Wrapper function ensures consistency

Bad:
- Same event fired from multiple places
- Inconsistent property population
```

**2. Server-Side When Possible**
```
Prefer Server-Side:
- Reliable delivery
- Harder to block
- Consistent timestamps
- Secure properties

Client-Side Only:
- UI interactions (clicks, scrolls)
- Performance metrics
- Error states
```

**3. Event Validation**
```
// Schema validation on send
const eventSchema = {
  project_created: {
    required: ['project_id', 'project_name', 'source'],
    properties: {
      project_id: { type: 'string' },
      project_name: { type: 'string', maxLength: 100 },
      source: { type: 'string', enum: ['dashboard', 'import', 'api'] }
    }
  }
};

// Validate before sending
validateAndSend(event, eventSchema);
```

### Event Planning Worksheet

| Question | Answer |
|----------|--------|
| **What behavior are we measuring?** | Project creation success |
| **What decisions will this inform?** | Onboarding optimization |
| **What's the trigger moment?** | Project saved to database |
| **What context is needed?** | Source, template, time |
| **Who owns implementation?** | Engineering team |
| **Who owns data quality?** | Analytics team |
| **When is this reviewed?** | Quarterly audit |

### Event Governance

**Tracking Plan Ownership:**
```
1. Product Manager defines requirements
2. Analyst defines event spec
3. Engineer implements
4. QA validates
5. Analyst monitors quality
6. All: Quarterly review
```

**Change Management:**
```
Adding event:
1. Create spec document
2. Review with stakeholders
3. Implement with tests
4. Validate in staging
5. Deploy and monitor

Changing event:
1. Document change reason
2. Version the event (v2)
3. Parallel track during transition
4. Migrate dashboards
5. Deprecate old version
```

### Anti-Patterns

- **Track everything** — Noise drowns signal, costs explode
- **Track nothing** — Flying blind, can't learn
- **Client-only** — Ad blockers, reliability issues
- **No schema** — Properties drift, data becomes unusable
- **No ownership** — Nobody maintains, quality degrades
- **Hardcoded strings** — Typos break tracking
- **Missing context** — Events without user/session info
- **No documentation** — Nobody knows what events mean
