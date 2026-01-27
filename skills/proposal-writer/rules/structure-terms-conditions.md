---
title: Terms & Conditions Positioning
impact: HIGH
tags: terms, conditions, legal, contract, negotiation
---

## Terms & Conditions Positioning

**Impact: HIGH**

Terms and conditions can kill deals or create unnecessary friction. Position them as partnership guardrails, not gotchas.

### The Terms Mindset

```
┌─────────────────────────────────────────────────────────────┐
│                    TERMS PHILOSOPHY                         │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│   WRONG: "How do we protect ourselves from the customer?"   │
│                                                             │
│   RIGHT: "How do we set up both parties for success?"       │
│                                                             │
│   Terms should reduce friction, not create it               │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

### Common Proposal Terms

| Term | Purpose | Customer Concern |
|------|---------|------------------|
| **Payment terms** | Cash flow | Budget cycles |
| **Contract length** | Commitment | Flexibility |
| **Auto-renewal** | Retention | Surprise charges |
| **Price increases** | Growth | Cost control |
| **Termination** | Exit options | Lock-in |
| **SLA** | Performance guarantee | Reliability |
| **Data ownership** | IP protection | Portability |
| **Liability caps** | Risk allocation | Protection |

### Good Example: Customer-Friendly Terms Section

```markdown
## Terms & Partnership Details

### Investment Summary
| Item | Amount |
|------|--------|
| Annual Platform License | $84,000 |
| One-Time Implementation | $12,000 |
| **Year 1 Total** | **$96,000** |
| **Renewal (Year 2+)** | **$84,000/year** |

### Payment Options

We offer flexible payment to accommodate your budget cycles:

| Option | Terms | Benefit |
|--------|-------|---------|
| **Annual prepay** | 100% at signing | 2 months free ($14K value) |
| **Semi-annual** | 50% at signing, 50% at month 6 | Budget flexibility |
| **Quarterly** | 25% each quarter | Spread over fiscal year |

### Contract Details

**Initial Term:** 12 months from go-live date

**Renewal:** Renews annually unless either party provides
60-day written notice. No auto-renewal surprises - we'll reach
out 90 days before to discuss.

**Price Protection:** Pricing locked for initial term. Any
renewal increases capped at 5% annually with 90-day notice.

### Service Level Agreement

| Metric | Commitment | Remedy |
|--------|------------|--------|
| Uptime | 99.95% monthly | Service credits |
| Response time (P1) | 1 hour | Escalation |
| Response time (P2) | 4 hours | — |
| Response time (P3) | 1 business day | — |

Service credits: 5% of monthly fee for each 0.1% below SLA,
up to 25% monthly maximum.

### Your Data, Your Control

- **Data ownership:** You retain full ownership of your data
- **Export:** Full data export available at any time in standard formats
- **Deletion:** Complete data deletion within 30 days of termination
- **Portability:** No proprietary formats; your data isn't held hostage

### Termination Rights

**For cause:** Either party may terminate with 30 days written
notice if material breach is not cured within that period.

**For convenience:** After initial 12-month term, cancel with
60 days written notice. Pro-rated refund for unused prepaid fees.

### Implementation Guarantee

If we don't achieve go-live within 60 days (per agreed timeline),
you receive:
- Extended implementation support at no charge
- 1 month free platform usage
- Right to terminate with full refund

We stand behind our delivery commitments.

---

*Full terms and conditions available in Master Service Agreement.
Key customer-friendly provisions summarized above.*
```

### Bad Example: Adversarial Terms Section

```markdown
## Terms and Conditions

1. Payment is due NET 30 from invoice date. Late payments accrue
   interest at 1.5% per month.

2. Contract auto-renews for successive 12-month terms unless
   terminated with 90 days written notice.

3. Pricing may increase up to 10% annually at Provider's discretion.

4. Provider may modify the platform at any time without notice.

5. Customer data will be retained for 12 months after termination
   unless deletion is requested in writing.

6. Provider liability is limited to fees paid in the prior 3 months.

7. Customer agrees to arbitration in Provider's home jurisdiction.

8. Customer grants Provider license to use Customer name and logo
   in marketing materials.

See attached Master Service Agreement for complete terms.
```

**Why it fails:**
- One-sided language
- Hidden gotchas (auto-renew, data retention)
- Adversarial tone
- Discretionary price increases
- No benefits to customer
- Reads like legal protection, not partnership

### Positioning Challenging Terms

**Auto-renewal:**
```
ADVERSARIAL: "Contract auto-renews unless cancelled"

PARTNERSHIP: "Your subscription continues uninterrupted at renewal.
We'll reach out 90 days before to review and discuss any changes.
Cancel with 60 days notice if things change."
```

**Payment terms:**
```
ADVERSARIAL: "Payment due NET 30. Late fees apply."

PARTNERSHIP: "Payment due 30 days from invoice. If you need different
terms to align with your budget cycle, let's discuss."
```

**Price increases:**
```
ADVERSARIAL: "Prices may increase up to 10% annually."

PARTNERSHIP: "Pricing is locked for your initial term. Renewals are
capped at 5% increase with 90 days advance notice - no surprises."
```

### SLA Best Practices

**Include meaningful SLAs:**
```
┌─────────────────────────────────────────────────────────────┐
│                    SLA COMPONENTS                           │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│   Availability     99.9% / 99.95% / 99.99%                  │
│   Response time    By severity level (P1/P2/P3)             │
│   Resolution time  Target, not guarantee                    │
│   Remedy           Service credits, not just apology        │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

**SLA calculation transparency:**
```markdown
**Uptime Calculation:**
- Measured monthly, calendar month basis
- Excludes scheduled maintenance (48-hour notice provided)
- Excludes customer-caused issues
- Measured at API endpoint level

**Example:**
43,200 minutes in 30-day month
99.95% = 21.6 minutes allowed downtime
```

### Data & Security Terms

**Customer data rights to include:**
```markdown
✓ Customer owns all data uploaded to platform
✓ Provider processes data only for service delivery
✓ Full export available in standard formats (JSON, CSV)
✓ Data deleted within 30 days of termination upon request
✓ Subprocessor list maintained and available
✓ Data processing agreement (DPA) available
✓ SOC 2 Type II report available under NDA
```

### Negotiation Points to Expect

| They Ask For | Your Options |
|--------------|--------------|
| Longer payment terms | Net 45/60 if prepaid annually |
| No auto-renew | Convert to manual renewal with reminder |
| Price cap on renewal | Cap at 3-5%, lock for multi-year |
| Broader termination | For convenience after Year 1 |
| Higher liability cap | 12 months fees (vs. 3 months) |
| Shorter notice period | 30 days (from 90) |
| Logo use removal | Approve case-by-case instead |

### Red Lines (Know Your Limits)

**Typical non-negotiables:**
- Unlimited liability
- Indemnification for customer's data misuse
- Custom SLAs without engineering approval
- Payment terms > 60 days without CFO approval
- No auto-renewal on monthly plans

**Process for exceptions:**
```
1. Escalate to legal/finance
2. Document customer rationale
3. Propose compromise
4. Get written approval for exception
5. Add to contract as amendment
```

### Presenting Terms in Proposals

**Placement:**
- After pricing (reader understands investment first)
- Before next steps (terms don't end the proposal)
- Summarize; don't include full MSA

**Tone:**
- Partnership language
- Customer benefits highlighted
- Commitments go both ways
- Plain English, not legalese

### Anti-Patterns

- **Burying terms** — Hidden on page 47 of MSA
- **Gotcha clauses** — Things that surprise customers post-signature
- **All-caps legal** — Aggressive formatting signals
- **One-sided language** — "Provider may... Customer shall..."
- **No flexibility** — Rigid terms lose deals
- **Missing key terms** — Forces last-minute negotiation
- **Legalese in proposal** — Save technical terms for MSA
