---
title: CRM Architecture & Data Model
impact: CRITICAL
tags: crm, architecture, data-model, salesforce, hubspot
---

## CRM Architecture & Data Model

**Impact: CRITICAL**

Your CRM data model determines what questions you can answer. Get the architecture right, and everything else becomes possible.

### Core Object Relationships

```
┌─────────────────────────────────────────────────────────────────┐
│                         ACCOUNT                                  │
│   (Company record - single source of truth for org data)        │
└───────────────────────────────┬─────────────────────────────────┘
                                │
         ┌──────────────────────┼──────────────────────┐
         │                      │                      │
         ▼                      ▼                      ▼
    ┌─────────┐           ┌─────────┐           ┌─────────┐
    │ CONTACT │           │  LEAD   │           │  OPP    │
    │(Converted│◄─────────│(Pre-    │           │(Deal in │
    │ leads)   │  Convert │qualified)│          │progress)│
    └─────────┘           └─────────┘           └─────────┘
         │                                            │
         │                                            │
         └──────────────► ACTIVITIES ◄────────────────┘
                    (Calls, emails, meetings)
```

### Object Design Principles

| Principle | Good Practice | Bad Practice |
|-----------|---------------|--------------|
| **Single source of truth** | Account holds company data | Duplicating company name on every contact |
| **Minimal custom objects** | Use standard objects when possible | Custom object for every process |
| **Clear ownership** | One owner per record | Multiple ownership fields |
| **Audit trail** | Created/Modified fields preserved | Overwriting historical data |

### Field Design Guidelines

**Do This:**
```
Field: Annual_Revenue__c
Type: Currency
Required: No
Help Text: "Company annual revenue in USD. Source: ZoomInfo or company disclosure."
Validation: Must be >= 0
```

**Not This:**
```
Field: Revenue
Type: Text (arbitrary format)
Required: Yes (blocks record creation)
Help Text: None
Validation: None (accepts "~5M" or "$5,000,000" or "5000000")
```

### Standard vs Custom Fields

| Use Standard Fields For | Use Custom Fields For |
|-------------------------|----------------------|
| Name, email, phone | Industry-specific attributes |
| Address, website | Calculated/derived values |
| Owner, created date | Integration mappings |
| Stage, amount, close date | Business-specific processes |

### Record Type Strategy

**When to use Record Types:**
- Different sales processes (New Business vs Expansion)
- Different page layouts needed
- Different picklist values by type
- Reporting segmentation requirements

**When NOT to use Record Types:**
- Just for filtering (use fields instead)
- Fewer than 100 records of a type
- No process differences

### Good Example: Clean Data Model

```
Account
├── Name (Standard)
├── Industry (Standard)
├── Annual_Revenue__c (Currency)
├── Employee_Count__c (Number)
├── ICP_Score__c (Formula: calculated)
├── Owner (Lookup to User)
└── Account_Tier__c (Picklist: Enterprise/Mid-Market/SMB)

Opportunity
├── Name (Standard)
├── Account (Lookup - required)
├── Stage (Standard picklist)
├── Amount (Standard currency)
├── Close_Date (Standard date)
├── Primary_Contact__c (Lookup to Contact)
├── Loss_Reason__c (Picklist - required if Closed Lost)
└── Competition__c (Multi-select picklist)
```

### Bad Example: Messy Data Model

```
Opportunity (Problematic)
├── Account_Name__c (Text - duplicates Account.Name)
├── Account_Industry__c (Text - duplicates Account.Industry)
├── Contact_Email__c (Text - should be lookup)
├── Stage__c (Text - should be picklist)
├── deal_size (Text - should be Currency)
├── Expected_Close (Text - should be Date)
├── won_lost (Checkbox - conflicts with Stage)
└── notes_misc_other_info (Long text - catch-all field)
```

### Data Model Audit Checklist

| Check | Pass Criteria |
|-------|---------------|
| No duplicate data across objects | Company data lives on Account only |
| Lookups instead of text references | Related records use relationship fields |
| Consistent naming conventions | All custom fields use `Field_Name__c` format |
| Required fields are truly required | Won't block legitimate record creation |
| Formula fields for derived values | No manual calculation required |
| Picklists have valid values only | No "Other" that's used 50% of the time |

### Integration Field Strategy

Always create dedicated fields for integration data:

```
Integration Fields (read-only to users):
├── ZoomInfo_ID__c
├── ZoomInfo_Last_Updated__c
├── Outreach_Sequence_Status__c
├── Gong_Last_Call_Date__c
└── Marketing_Attribution_Source__c
```

### Anti-Patterns

- **Field sprawl** — Creating new fields without auditing existing ones
- **Text field abuse** — Using text for dates, currencies, lookups
- **Required field overload** — Making everything required blocks adoption
- **Lookup vs Master-Detail confusion** — Wrong relationship type causes data issues
- **No naming convention** — `revenue`, `Revenue__c`, `Annual_Rev`, `ACV` all meaning the same thing
- **Catch-all fields** — "Notes" or "Other Info" fields become data graveyards
