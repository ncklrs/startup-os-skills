---
title: Platform Metrics and Health
impact: CRITICAL
tags: metrics, analytics, health, monitoring, kpis
---

## Platform Metrics and Health

**Impact: CRITICAL**

What you measure defines what you improve. Platform health metrics span technical reliability, developer experience, and business outcomes.

### The Platform Metrics Hierarchy

```
┌─────────────────────────────────────────────────────────────┐
│                    BUSINESS METRICS                         │
│    Revenue • NDR • Customer Count • Expansion Revenue       │
├─────────────────────────────────────────────────────────────┤
│                   DEVELOPER METRICS                         │
│    MAD • API Calls • Retention • Use Cases Completed        │
├─────────────────────────────────────────────────────────────┤
│                  EXPERIENCE METRICS                         │
│    TTFC • Activation • Support Tickets • CSAT              │
├─────────────────────────────────────────────────────────────┤
│                   PLATFORM METRICS                          │
│    Uptime • Latency • Error Rate • Throughput              │
└─────────────────────────────────────────────────────────────┘
```

### Core Platform Health Metrics

| Metric | Definition | Target | Alert Threshold |
|--------|------------|--------|-----------------|
| **Uptime** | Available time / Total time | 99.9%+ | < 99.5% |
| **P50 Latency** | Median response time | < 100ms | > 200ms |
| **P99 Latency** | 99th percentile response | < 500ms | > 1000ms |
| **Error Rate** | Errors / Total requests | < 0.1% | > 1% |
| **Throughput** | Requests per second | Baseline | 50% drop |

### Developer Experience Metrics

| Metric | Formula | Target | How to Measure |
|--------|---------|--------|----------------|
| **Time to First Call (TTFC)** | Signup → First API call | < 15 min | Event tracking |
| **Activation Rate** | Made API call / Signups | > 50% | Funnel analysis |
| **Day 7 Retention** | Active day 7 / Signups | > 25% | Cohort analysis |
| **Day 30 Retention** | Active day 30 / Signups | > 15% | Cohort analysis |
| **Support Ticket Rate** | Tickets / Active developers | < 5% | Support data |

### Business Metrics for Platforms

| Metric | Definition | Target | Calculation |
|--------|------------|--------|-------------|
| **MAD** | Monthly Active Developers | Growth | Unique developers with API calls |
| **API Call Volume** | Total monthly API calls | Growth | Sum all requests |
| **Revenue per Developer** | MRR / MAD | Stable/growth | Financial / usage data |
| **Net Dollar Retention** | Expansion - Churn | > 110% | Revenue tracking |
| **Logo Retention** | Customers retained | > 90% | Customer count |

### Developer Funnel Metrics

```
Stage               Metric                    Target
─────────────────────────────────────────────────────
AWARENESS           Site visits               Growth
                    Docs visits               Growth
    │
    ▼
SIGNUP              Signups                   Growth
                    Signup conversion         > 5%
    │
    ▼
ACTIVATION          API key generated         > 80% of signups
                    First API call            > 50% of signups
    │
    ▼
ENGAGEMENT          Weekly active             > 30% of activated
                    API calls/developer       Growing
    │
    ▼
EXPANSION           Upgrade rate              > 10%
                    API volume growth         > 20% MoM
    │
    ▼
ADVOCACY            Referrals                 Growing
                    Community contributions   Growing
```

### SLA Definitions

**Standard SLA tiers:**

| Tier | Uptime | Support Response | Use Case |
|------|--------|------------------|----------|
| **Basic** | 99.5% | 24h | Free, starter |
| **Pro** | 99.9% | 4h business hours | Growth |
| **Enterprise** | 99.99% | 1h, 24/7 | Critical infrastructure |

**SLA calculation:**

```
Monthly Uptime = (Total Minutes - Downtime Minutes) / Total Minutes

43,200 minutes in a month (30 days)

99.9% = max 43 minutes downtime
99.95% = max 22 minutes downtime
99.99% = max 4 minutes downtime
```

### Error Rate Analysis

**Track errors by category:**

| Category | Example Codes | Owner | Action |
|----------|---------------|-------|--------|
| **Client errors** | 400, 401, 403, 404, 422 | Developer | Better docs, validation |
| **Server errors** | 500, 502, 503 | Engineering | Fix bugs, scale |
| **Rate limits** | 429 | Product | Adjust limits, offer upgrades |
| **Timeouts** | 504 | Engineering | Optimize, scale |

**Error budget:**

```
Error Budget = 1 - SLA

For 99.9% SLA:
Error budget = 0.1% of requests can fail
Or ~43 minutes downtime/month
```

### API Usage Dashboards

**Essential dashboard views:**

| Dashboard | Metrics | Audience |
|-----------|---------|----------|
| **Real-time** | Requests/sec, errors, latency | On-call engineering |
| **Daily health** | Uptime, P99, error rate | Engineering leads |
| **Developer activity** | TTFC, activation, retention | Product |
| **Business** | MAD, revenue, growth | Leadership |
| **Customer-facing** | Status page | All users |

### Cohort Analysis for Developers

**Track developer cohorts over time:**

```
         Week 0   Week 1   Week 2   Week 4   Week 8
Jan '24   100%     45%      32%      25%      20%
Feb '24   100%     52%      38%      30%      24%
Mar '24   100%     58%      45%      35%      28%
                   ↑
          Week-over-week improvement shows
          onboarding changes working
```

### Rate Limiting Metrics

| Metric | Purpose | Target |
|--------|---------|--------|
| **Rate limit hits** | Capacity planning | < 1% of requests |
| **Developers hitting limits** | Pricing/limits fit | < 5% |
| **Limit → upgrade rate** | Monetization | > 10% |
| **Limit → churn rate** | Friction indicator | < 5% |

### Developer Satisfaction Metrics

| Metric | Collection Method | Frequency | Target |
|--------|-------------------|-----------|--------|
| **NPS** | In-product survey | Quarterly | > 50 |
| **CSAT** | Post-support survey | Per ticket | > 4.5/5 |
| **CES** | Task completion survey | Per flow | < 2 (low effort) |
| **Developer feedback** | Community, support | Continuous | Qualitative |

### Alerting Strategy

**Alert priority levels:**

| Level | Response Time | Example | Notification |
|-------|---------------|---------|--------------|
| **P1 - Critical** | < 15 min | Full outage | Page, all channels |
| **P2 - High** | < 1 hour | Partial outage | Page on-call |
| **P3 - Medium** | < 4 hours | Degraded performance | Slack alert |
| **P4 - Low** | Next business day | Anomaly detected | Email digest |

### Metric Review Cadence

| Cadence | Metrics | Attendees |
|---------|---------|-----------|
| **Real-time** | Uptime, errors, latency | On-call |
| **Daily** | API health, support queue | Eng leads |
| **Weekly** | Developer funnel, activation | Product team |
| **Monthly** | MAD, retention, business | Leadership |
| **Quarterly** | NPS, satisfaction, strategy | Exec + Product |

### Anti-Patterns

- **Vanity metrics** — Tracking total users not active users
- **No segmentation** — Same metrics for all developer types
- **Lagging only** — No leading indicators
- **Alert fatigue** — Too many non-actionable alerts
- **No benchmarks** — Metrics without targets
- **Metric silos** — Platform and business metrics disconnected
- **Gaming metrics** — Optimizing metric not outcome
- **Invisible failures** — Not tracking silent errors
- **Missing cohorts** — Aggregate only, no time-based analysis
