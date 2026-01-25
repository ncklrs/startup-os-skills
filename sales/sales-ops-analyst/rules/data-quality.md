---
title: Data Quality Management
impact: HIGH
tags: data, quality, deduplication, enrichment, governance
---

## Data Quality Management

**Impact: HIGH**

Bad data is worse than no data. It leads to wrong decisions, wasted effort, and lost trust. Data quality is everyone's job, but ops owns the system.

### Data Quality Dimensions

| Dimension | Definition | Example Problem |
|-----------|------------|-----------------|
| **Accuracy** | Data reflects reality | Company has 50 employees, CRM says 5,000 |
| **Completeness** | Required fields populated | 40% of accounts missing industry |
| **Consistency** | Same data, same format | "IBM", "I.B.M.", "International Business Machines" |
| **Timeliness** | Data is current | Contact left company 2 years ago |
| **Validity** | Data meets business rules | Email format: user@domain.com |
| **Uniqueness** | No duplicates | Same company appears 5 times |

### Data Quality Scorecard

```
┌────────────────────────────────────────────────────────────┐
│               DATA QUALITY SCORECARD - ACCOUNTS            │
├────────────────────────────────────────────────────────────┤
│                                                             │
│ Overall Score: 78% (Target: >90%)                          │
│                                                             │
│ ┌──────────────────────────────────────────────────────┐  │
│ │ Dimension        Score   Trend   Target   Gap       │  │
│ ├──────────────────────────────────────────────────────┤  │
│ │ Accuracy         85%     ↑       90%      -5%       │  │
│ │ Completeness     72%     →       95%      -23%  ⚠️  │  │
│ │ Consistency      81%     ↑       85%      -4%       │  │
│ │ Timeliness       65%     ↓       80%      -15%  ⚠️  │  │
│ │ Validity         92%     →       95%      -3%       │  │
│ │ Uniqueness       88%     ↑       95%      -7%       │  │
│ └──────────────────────────────────────────────────────┘  │
│                                                             │
│ Critical Issues:                                            │
│ • 2,340 accounts missing industry (23% incomplete)         │
│ • 1,850 contacts with bounce rate >20% (stale data)       │
│ • 456 duplicate account pairs detected                      │
└────────────────────────────────────────────────────────────┘
```

### Deduplication Strategy

**Matching Rules Hierarchy:**

```
Match Confidence Levels:

EXACT MATCH (auto-merge):
├── Same Domain + Same Name
├── Same DUNS number
└── Same External ID (from integration)

HIGH CONFIDENCE (review queue):
├── Same Domain + Similar Name (Levenshtein <3)
├── Same Phone + Same City
└── Same Address + Similar Name

POSSIBLE MATCH (manual review):
├── Similar Name + Same Industry + Same City
├── Same Email domain pattern
└── Parent/Subsidiary relationship detected
```

**Deduplication Process:**

```python
# Duplicate detection logic
def find_duplicates(accounts):
    duplicates = []

    # Step 1: Exact domain match
    domain_groups = group_by(accounts, 'website_domain')
    for domain, accts in domain_groups.items():
        if len(accts) > 1:
            duplicates.append({
                'type': 'exact_domain',
                'confidence': 'high',
                'accounts': accts
            })

    # Step 2: Fuzzy name match
    for i, acct1 in enumerate(accounts):
        for acct2 in accounts[i+1:]:
            similarity = name_similarity(acct1.name, acct2.name)
            if similarity > 0.85:
                duplicates.append({
                    'type': 'fuzzy_name',
                    'confidence': 'medium',
                    'similarity': similarity,
                    'accounts': [acct1, acct2]
                })

    return duplicates

# Merge strategy
def merge_accounts(master, duplicate):
    """Keep master record, enrich with duplicate data"""
    for field in ENRICHMENT_FIELDS:
        if not master.get(field) and duplicate.get(field):
            master[field] = duplicate[field]

    # Reparent all child records
    reparent_contacts(duplicate.id, master.id)
    reparent_opportunities(duplicate.id, master.id)
    reparent_activities(duplicate.id, master.id)

    # Mark duplicate as merged
    duplicate.status = 'Merged'
    duplicate.merged_into = master.id
```

### Data Enrichment Sources

| Source | Data Types | Accuracy | Cost |
|--------|------------|----------|------|
| **ZoomInfo** | Company, contacts, intent | High | $$$ |
| **Clearbit** | Company firmographics | High | $$ |
| **Apollo** | Company, contacts, email | Medium-High | $$ |
| **LinkedIn Sales Nav** | Contacts, job changes | High | $$ |
| **Crunchbase** | Funding, news | High | $ |
| **BuiltWith** | Tech stack | High | $$ |
| **6sense/Bombora** | Intent data | Medium | $$$ |

### Validation Rules

**Field-Level Validation:**

| Field | Validation Rule | Error Message |
|-------|-----------------|---------------|
| Email | Regex: `^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$` | "Invalid email format" |
| Phone | Strip non-digits, length 10-15 | "Invalid phone number" |
| Website | Must start with http(s):// or add it | "Include full URL" |
| Annual Revenue | Must be >= 0 | "Revenue cannot be negative" |
| Employee Count | Must be >= 1 | "Must have at least 1 employee" |
| Country | Must be in ISO 3166-1 list | "Select valid country" |

**Cross-Field Validation:**

```apex
// Salesforce validation rule: Close Date consistency
AND(
  ISPICKVAL(StageName, "Closed Won"),
  CloseDate > TODAY()
)
// Error: "Closed Won deals cannot have future close dates"

// Validation: Loss reason required
AND(
  ISPICKVAL(StageName, "Closed Lost"),
  ISBLANK(Loss_Reason__c)
)
// Error: "Loss reason is required for Closed Lost opportunities"
```

### Data Governance Program

**RACI Matrix for Data Quality:**

| Activity | Sales Ops | Reps | Managers | IT |
|----------|-----------|------|----------|-----|
| Define data standards | A | C | C | R |
| Monitor quality metrics | R | - | I | C |
| Fix data issues | A | R | R | C |
| Build validation rules | R | C | C | A |
| Enrichment strategy | R | - | C | A |
| Duplicate resolution | R | C | A | - |

*R=Responsible, A=Accountable, C=Consulted, I=Informed*

**Data Quality SLAs:**

| Metric | Target | Measurement |
|--------|--------|-------------|
| New lead completeness | >90% within 24h | Required fields populated |
| Duplicate rate | <5% | Weekly duplicate scan |
| Email bounce rate | <10% | Monthly email validation |
| Data enrichment | >80% of new accounts | Weekly enrichment job |
| Stale contact rate | <15% | Contacts not updated in 180 days |

### Data Cleanup Workflow

```
Weekly Data Quality Process:

Monday:
├── Run duplicate detection job
├── Generate quality scorecard
└── Assign cleanup tasks

Tuesday-Thursday:
├── Reps review/update their accounts (30 min/week)
├── Ops processes duplicate queue
└── Enrichment jobs run overnight

Friday:
├── Review week's progress
├── Update quality metrics
└── Plan next week's focus areas
```

### Common Data Quality Issues & Fixes

| Issue | Detection | Fix |
|-------|-----------|-----|
| Duplicate accounts | Weekly matching job | Merge with master record selection |
| Missing fields | Report on NULL values | Enrichment + rep outreach |
| Invalid emails | Bounce tracking | Email verification service |
| Stale contacts | No activity >180 days | Re-verification campaign |
| Inconsistent naming | Standardization report | Find/replace + future validation |
| Orphaned contacts | No account association | Match to accounts or delete |

### Anti-Patterns

- **No data owner** — Everyone's job is no one's job
- **Blame without tools** — Expecting reps to fix data without help
- **One-time cleanup** — Data quality is ongoing, not a project
- **Over-required fields** — Blocking record creation causes workarounds
- **No enrichment** — Relying solely on manual data entry
- **Ignoring duplicates** — "We'll fix it later" becomes never
- **Validation without context** — Rules that don't explain the "why"
- **No measurement** — If you don't measure it, you can't improve it
