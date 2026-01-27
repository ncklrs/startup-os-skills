---
title: Lead Routing & Assignment
impact: HIGH
tags: routing, assignment, leads, territory, round-robin
---

## Lead Routing & Assignment

**Impact: HIGH**

Speed to lead is everything. The first vendor to respond wins 35-50% of deals. Your routing rules can be the difference between a closed deal and a lost opportunity.

### Speed to Lead Benchmarks

| Response Time | Conversion Impact |
|---------------|-------------------|
| <5 minutes | Optimal conversion rate |
| 5-30 minutes | 21x less likely to qualify than <5 min |
| >30 minutes | Dramatic drop-off |
| >1 hour | Lead is likely cold |

### Routing Logic Hierarchy

```
                    ┌─────────────────────┐
                    │    INBOUND LEAD     │
                    └──────────┬──────────┘
                               │
                    ┌──────────▼──────────┐
            ┌───────│  Existing Account?  │───────┐
            │       └─────────────────────┘       │
           YES                                    NO
            │                                     │
            ▼                                     ▼
    ┌───────────────┐                   ┌───────────────┐
    │ Route to      │                   │ Apply lead    │
    │ Account Owner │                   │ scoring       │
    └───────────────┘                   └───────┬───────┘
                                                │
                                    ┌───────────▼───────────┐
                            ┌───────│   Score >= MQL?       │───────┐
                            │       └───────────────────────┘       │
                           YES                                      NO
                            │                                       │
                            ▼                                       ▼
                    ┌───────────────┐                     ┌───────────────┐
                    │ Territory     │                     │ Marketing     │
                    │ assignment    │                     │ nurture       │
                    └───────┬───────┘                     └───────────────┘
                            │
                            ▼
                    ┌───────────────┐
                    │ Round-robin   │
                    │ within region │
                    └───────────────┘
```

### Assignment Rule Types

| Type | Best For | Complexity | Example |
|------|----------|------------|---------|
| **Territory-based** | Geographic/named account coverage | Medium | "West Coast > California > Bay Area > Sarah" |
| **Round-robin** | Equal distribution | Low | Rotate through available reps |
| **Weighted round-robin** | Performance/capacity-based | Medium | "Top rep gets 2x leads" |
| **Lead score-based** | Prioritize hot leads | High | "Score >80 → Enterprise team" |
| **Product-based** | Multiple products | Medium | "Enterprise product → Enterprise SDR" |

### Round-Robin Implementation

**Good Example: Fair & Trackable**

```python
# Weighted round-robin with capacity tracking
assignment_rules = {
    "enterprise_team": {
        "members": [
            {"name": "Sarah", "weight": 2, "max_daily": 10, "current": 3},
            {"name": "Mike", "weight": 1, "max_daily": 8, "current": 5},
            {"name": "Lisa", "weight": 1.5, "max_daily": 12, "current": 7}
        ],
        "logic": "weighted_round_robin",
        "overflow": "queue_for_manager"
    }
}

# Assignment logic
def assign_lead(lead, team):
    available = [m for m in team["members"] if m["current"] < m["max_daily"]]
    if not available:
        return team["overflow"]

    # Weighted selection based on remaining capacity
    weights = [(m["max_daily"] - m["current"]) * m["weight"] for m in available]
    return weighted_random(available, weights)
```

**Bad Example: Unfair Distribution**

```python
# First-come, first-served (creates inequality)
def assign_lead(lead):
    for rep in all_reps:
        if rep.is_online():
            return rep  # Always assigns to same fast rep
```

### Territory Design Framework

**Balanced Territory Criteria:**

| Factor | Weight | Measurement |
|--------|--------|-------------|
| Revenue potential | 40% | TAM of accounts in territory |
| Account volume | 25% | Number of target accounts |
| Historical performance | 20% | Win rate, cycle time |
| Geographic spread | 15% | Travel time/zones |

**Territory Assignment Example:**

```
Region: West
├── Enterprise (>1000 employees)
│   ├── Named Accounts: [Fortune 500 list]
│   └── Owner: Senior AE (Sarah)
│
├── Mid-Market (100-999 employees)
│   ├── States: CA, OR, WA
│   ├── Industries: Tech, Healthcare
│   └── Owner: AE (Mike)
│
└── SMB (<100 employees)
    ├── Inbound only
    ├── Round-robin assignment
    └── Team: SMB AE Pool
```

### Lead Routing Rules Matrix

| Condition | Company Size | Lead Source | Assignment |
|-----------|--------------|-------------|------------|
| Named Account | Any | Any | Account Owner |
| Enterprise | >1000 emp | Demo Request | Enterprise AE |
| Enterprise | >1000 emp | Content | Enterprise SDR |
| Mid-Market | 100-999 | Demo Request | MM AE (territory) |
| Mid-Market | 100-999 | Content | MM SDR |
| SMB | <100 | Demo Request | SMB AE (round-robin) |
| SMB | <100 | Content | Marketing nurture |

### SLA Monitoring

**Response SLA Table:**

| Lead Type | Target Response | Alert Threshold | Escalation |
|-----------|-----------------|-----------------|------------|
| Demo Request | <5 min | 10 min | Manager |
| Trial Signup | <1 hour | 2 hours | Manager |
| Content Download | <4 hours | 8 hours | Team Lead |
| Event Lead | <24 hours | 48 hours | SDR Manager |

**SLA Dashboard Metrics:**

```
┌────────────────────────────────────────────────┐
│           LEAD RESPONSE SLA DASHBOARD           │
├────────────────────────────────────────────────┤
│ Today's Leads: 47                              │
│ ┌──────────────────────────────────────────┐  │
│ │ Met SLA (<5min):    ████████████ 78% (37)│  │
│ │ Warning (5-15min):  ████ 15% (7)         │  │
│ │ Breached (>15min):  ██ 7% (3)            │  │
│ └──────────────────────────────────────────┘  │
│                                                │
│ Avg Response Time: 4.2 min (Target: <5 min)   │
│ Leads in Queue Now: 2                          │
│ Oldest Uncontacted: 3 min                      │
└────────────────────────────────────────────────┘
```

### Edge Case Handling

| Scenario | Rule |
|----------|------|
| Rep on PTO | Skip in rotation, reassign open leads |
| Territory conflict | Account owner > territory > round-robin |
| No matching rule | Assign to manager queue, alert ops |
| Duplicate lead | Merge with existing, notify owner |
| Invalid data | Route to data quality queue |

### Assignment Automation Code

```apex
// Salesforce Apex example: Territory-based with round-robin fallback
public class LeadAssignmentHandler {

    public static User assignLead(Lead lead) {
        // Step 1: Check for existing account owner
        Account existingAccount = findMatchingAccount(lead);
        if (existingAccount != null && existingAccount.OwnerId != null) {
            return existingAccount.Owner;
        }

        // Step 2: Find territory match
        Territory territory = TerritoryService.findTerritory(
            lead.State,
            lead.Industry,
            lead.Company_Size__c
        );

        if (territory != null) {
            // Step 3: Round-robin within territory
            return RoundRobinService.getNextRep(territory.Id);
        }

        // Step 4: Fallback to manager queue
        return [SELECT Id FROM User WHERE Name = 'Lead Queue Manager' LIMIT 1];
    }
}
```

### Anti-Patterns

- **Cherry-picking** — Reps choosing their own leads
- **Static assignment** — No adjustment for rep capacity or PTO
- **No SLA tracking** — Leads sitting for hours uncontacted
- **Over-complicated rules** — 50 rule variations impossible to maintain
- **No fallback** — Leads fall through cracks when rules don't match
- **Manual override abuse** — Managers reassigning based on favoritism
- **No audit trail** — Can't explain why lead went to which rep
