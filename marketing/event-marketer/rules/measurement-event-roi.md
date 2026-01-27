---
title: Event ROI Measurement
impact: HIGH
tags: measurement, roi, attribution, metrics, analytics
---

## Event ROI Measurement

**Impact: HIGH**

Events are expensive. Without rigorous measurement, you can't optimize, justify investment, or prove value. The companies that measure well spend more effectively than those flying blind.

### Event ROI Formula

```
Event ROI = (Revenue Attributed - Total Event Cost) / Total Event Cost × 100

Example:
- Total Event Cost: $50,000
- Revenue Attributed: $200,000
- ROI = ($200,000 - $50,000) / $50,000 × 100 = 300%
```

### Cost Categories to Track

| Category | Components | Often Missed |
|----------|------------|--------------|
| **Sponsorship** | Booth, speaking, branding | Package inclusions value |
| **Booth** | Design, production, shipping, storage | Design amortization |
| **Materials** | Collateral, swag, demos | Swag per-unit cost |
| **Travel** | Flights, hotels, meals, transport | Per diems, incidentals |
| **People** | Staff time, opportunity cost | Loaded cost, not just salary |
| **Marketing** | Pre/post event campaigns, ads | Production costs |
| **Technology** | Lead capture, demos, A/V | Platform fees |
| **Contingency** | Overages, emergencies | Always underestimated |

### Full Event Cost Calculation

```
Direct Costs:
├── Sponsorship/Registration     $30,000
├── Booth build + shipping       $15,000
├── Collateral + swag            $5,000
├── Technology                   $2,000
└── Pre/Post marketing           $3,000
                                 ────────
                                 $55,000

Travel Costs (6 people × 4 days):
├── Flights                      $9,000
├── Hotels                       $6,000
├── Meals + transport            $3,000
└── Incidentals                  $500
                                 ────────
                                 $18,500

People Cost (loaded hourly × hours):
├── Pre-event prep (40 hrs)      $4,000
├── Event days (192 hrs)         $19,200
├── Post-event follow-up (20 hrs) $2,000
                                 ────────
                                 $25,200

TOTAL TRUE COST:                 $98,700
(vs. the "$30k sponsorship" you quoted)
```

### Revenue Attribution Models

| Model | How It Works | Best For |
|-------|--------------|----------|
| **First-touch** | Event gets full credit if first interaction | Brand awareness events |
| **Last-touch** | Event gets full credit if last before close | Conversion events |
| **Multi-touch** | Event gets partial credit in journey | Long sales cycles |
| **Influenced** | Event touched the deal anywhere | Full picture |
| **Sourced** | Event was first touch AND won | Strict attribution |

### Attribution Lookback Windows

| Sales Cycle Length | Lookback Window | Rationale |
|-------------------|-----------------|-----------|
| **<30 days** | 30 days | Quick cycles, short memory |
| **30-90 days** | 90 days | Standard B2B |
| **90-180 days** | 180 days | Mid-market |
| **180+ days** | 365 days | Enterprise |

### Pipeline vs Revenue Metrics

| Metric | What It Measures | When to Use |
|--------|------------------|-------------|
| **MQLs generated** | Volume of interest | Immediate event success |
| **SQLs generated** | Quality of interest | 30-60 days post-event |
| **Meetings booked** | Engagement quality | Immediate-30 days |
| **Pipeline created** | Potential revenue | 30-90 days post-event |
| **Pipeline influenced** | Touch in journey | 90-180 days post-event |
| **Revenue closed** | Actual ROI | 180-365 days post-event |
| **Revenue influenced** | Broader impact | 180-365 days post-event |

### Event Metrics Dashboard

```
Event: SaaStr Annual 2024
Cost: $98,700
─────────────────────────────────────────────

Immediate Metrics (Week 1):
├── Badge scans:           847
├── Qualified conversations: 156
├── Meetings booked:        34
└── Hot leads:              28

Pipeline Metrics (Day 90):
├── MQLs generated:         89
├── SQLs generated:         32
├── Pipeline sourced:       $380,000
└── Pipeline influenced:    $1,200,000

Revenue Metrics (Day 180):
├── Closed won (sourced):   $95,000
├── Closed won (influenced): $340,000
└── Expected close (90 days): $180,000

ROI Calculations:
├── Sourced ROI:           -4% (break even ~$100k)
├── Influenced ROI:        244%
├── Cost per MQL:          $1,109
├── Cost per SQL:          $3,084
└── Cost per meeting:      $2,903
```

### Benchmarks by Event Type

| Event Type | Cost per MQL | Cost per SQL | Target ROI |
|------------|--------------|--------------|------------|
| **Tier 1 Conference** | $500-1500 | $1500-4000 | 3-5x (influenced) |
| **Industry Trade Show** | $300-800 | $1000-2500 | 5-8x |
| **Webinar** | $50-150 | $200-500 | 10-20x |
| **Virtual Summit** | $100-300 | $400-1000 | 8-15x |
| **Executive Dinner** | $200-500 | $500-1500 | 5-10x |
| **User Conference** | N/A | N/A | Retention/expansion |

### Tracking Implementation

| Data Point | Capture Method | System |
|------------|----------------|--------|
| **Lead source** | UTM, badge scan, form | CRM |
| **Event attended** | Registration, check-in | Event platform |
| **Sessions attended** | Session scan, app | Event platform |
| **Booth interaction** | Badge scan, form | Lead capture |
| **Content downloaded** | Gated assets | Marketing automation |
| **Meetings held** | Calendar, CRM | CRM |
| **Pipeline stage** | Sales process | CRM |
| **Deal attribution** | Multi-touch model | CRM/BI tool |

### CRM Setup for Event Attribution

```
Lead/Contact Fields:
├── Original lead source = "Event"
├── Lead source detail = "SaaStr 2024"
├── Event date = "2024-09-10"
├── Event interaction type = "Booth + Session"
└── Event lead score = "Hot"

Opportunity Fields:
├── Primary campaign = [Event Campaign]
├── Influenced campaigns = [Multiple events]
└── First touch = "Event - SaaStr 2024"

Campaign Hierarchy:
├── Events (Parent)
│   ├── Conferences (Parent)
│   │   ├── SaaStr 2024 (Campaign)
│   │   │   ├── Booth (Child)
│   │   │   ├── Speaking (Child)
│   │   │   └── Dinner (Child)
```

### Reporting Cadence

| Report | Frequency | Audience | Content |
|--------|-----------|----------|---------|
| **Event summary** | Week after event | Marketing, Sales | Leads, meetings, feedback |
| **Pipeline report** | Monthly | Leadership | Pipeline by event, trending |
| **Quarterly review** | Quarterly | Exec team | ROI, budget reallocation |
| **Annual analysis** | Yearly | Board/Exec | Full ROI, year-over-year |

### Good Measurement Practices

```
✓ Define success metrics BEFORE the event
  → What does good look like? Write it down.

✓ Track both sourced AND influenced
  → Sourced alone undervalues brand events

✓ Use consistent attribution model
  → Don't change methodology between events

✓ Compare like with like
  → Webinar CPL shouldn't compete with conference CPL

✓ Long-term tracking
  → Enterprise deals take 12+ months, measure accordingly

✓ Include opportunity cost
  → What else could that $100k and 6 people have done?
```

### Bad Measurement Practices

```
✗ Only counting badge scans
  → Volume without quality is meaningless

✗ Only measuring sourced revenue
  → Ignores 80% of event impact

✗ 30-day attribution window for enterprise
  → Sales cycle is 6 months, you're missing revenue

✗ Comparing webinar to conference ROI
  → Different investment, different purpose, different timeline

✗ Ignoring people costs
  → "Free" internal resources aren't free

✗ Waiting too long to measure
  → Day 180 numbers require Day 1 tracking
```

### Event Comparison Framework

| Dimension | How to Compare | Watch Out For |
|-----------|----------------|---------------|
| **Cost per MQL** | Same lead definition | Quality variance |
| **Cost per SQL** | Same qualification criteria | Timing variance |
| **Pipeline per $ spent** | Same attribution model | Sales cycle variance |
| **ROI** | Same time window | Deal size variance |
| **Brand impact** | Social, press, NPS | Hard to quantify |

### Event Investment Decision Matrix

```
                    High ROI
                        │
           ┌────────────┼────────────┐
           │ Scale      │ Invest     │
           │ (Do more)  │ (Double    │
Low Cost ──┼────────────┼────────────┼── High Cost
           │ Test       │ Optimize   │
           │ (Experiment│ or Cut     │
           └────────────┼────────────┘
                        │
                    Low ROI

Actions:
- Invest: High ROI, high cost → worth the spend
- Scale: High ROI, low cost → do more
- Optimize: Low ROI, high cost → fix or cut
- Test: Low ROI, low cost → experiment more
```

### Post-Event Learning Template

| Question | Answer | Action |
|----------|--------|--------|
| Did we hit lead goals? | Y/N + why | Adjust expectations or execution |
| Did we hit quality goals? | Y/N + why | Refine targeting or qualification |
| What worked best? | Specifics | Replicate |
| What didn't work? | Specifics | Change or stop |
| Unexpected learnings? | Observations | Incorporate |
| Would we do it again? | Y/N + conditions | Inform next year |

### Anti-Patterns

- **Badge scan counting** — Vanity metric without qualification
- **Sourced-only attribution** — Missing 60-80% of value
- **Short attribution windows** — Missing revenue in long cycles
- **No pre-defined success criteria** — Can't fail if you didn't set goals
- **Ignoring full cost** — Makes ROI look artificially good
- **Inconsistent measurement** — Can't compare events year over year
- **Delaying tracking setup** — Measuring after the fact is impossible
- **Measuring once** — Events compound, measure over years
