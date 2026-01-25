---
title: Demo Environment Preparation
impact: HIGH
tags: environment, preparation, setup, sandbox
---

## Demo Environment Preparation

**Impact: HIGH**

A flawless demo environment is invisible. A broken one destroys credibility. Invest the preparation time — the best demo content can't survive a crashing environment.

### Environment Types Comparison

| Environment | Best For | Effort | Risk | Authenticity |
|-------------|----------|--------|------|--------------|
| **Production** | Confident product, simple demos | Low | High | Highest |
| **Sandbox/Demo Instance** | Complex demos, new features | Medium | Low | Medium |
| **Customer Data (Anonymized)** | Late-stage, POC prep | High | Medium | Very High |
| **Recorded Video** | Consistency, unreliable features | Medium | None | Low |
| **Hybrid** | Cover all bases | High | Varies | Medium-High |

### The Demo Environment Checklist

**24 Hours Before:**

```
ENVIRONMENT
□ Demo instance is accessible and stable
□ All features to be shown are working
□ Data is current, realistic, and appropriate
□ No embarrassing content (test data, inappropriate names)
□ Correct branding/customer logo if personalized
□ Backup environment ready

ACCOUNTS
□ Demo user account works
□ Password known and saved
□ MFA configured and accessible
□ Correct permission levels set

INTEGRATIONS
□ All integrations connected and active
□ Test data flowing correctly
□ No stale/broken connections

TECHNICAL
□ Browser cleared of sensitive tabs/bookmarks
□ Browser extensions disabled
□ Notifications disabled (all apps)
□ Do Not Disturb enabled
□ Bandwidth tested
```

**1 Hour Before:**

```
FINAL CHECKS
□ Full run-through completed
□ Environment responds quickly
□ All screens load correctly
□ Data hasn't changed unexpectedly
□ Backup video/screenshots accessible
□ Notes and script ready

MACHINE PREP
□ Unnecessary applications closed
□ Desktop cleared or hidden
□ Resolution set correctly
□ Audio/video tested (if remote)
□ Backup power/internet ready
```

### Demo Data Strategy

**The "Goldilocks" Principle:**
- Not too sparse (looks unused)
- Not too dense (overwhelming)
- Just right (realistic, relevant)

**Data Volume by Demo Type:**

| Demo Type | Users | Records | Activity |
|-----------|-------|---------|----------|
| **Teaser** | 3-5 | Minimal | Last 24h |
| **Discovery** | 10-20 | Moderate | Last week |
| **Full Demo** | 50+ | Substantial | Last month |
| **POC** | Match their scale | Match their scale | Full history |

**Data Quality Checklist:**

```
□ Names are realistic (not "Test User 1")
□ Company names are appropriate (not competitors)
□ Numbers make sense (not $999,999,999)
□ Dates are current (not 2019 timestamps)
□ Status distributions are realistic
□ No PII or sensitive data
□ No inside jokes or inappropriate content
```

### Scenario Pre-Loading

**Pre-stage these for common demo flows:**

| Scenario | Pre-Load |
|----------|----------|
| **Report generation** | Complex report ready to generate |
| **Workflow automation** | Trigger ready to execute |
| **Search demonstration** | Known-good search terms |
| **Notification flow** | User configured to receive notification |
| **Integration demo** | Connected system ready to sync |

### Live vs Sandbox Decision Matrix

```
Choose PRODUCTION when:
□ Product is very stable
□ Demo is straightforward
□ Performance matters
□ Customer wants "real" feel
□ Data doesn't need customization

Choose SANDBOX when:
□ Showing new/beta features
□ Complex multi-step workflows
□ Customer-specific configuration needed
□ Risk tolerance is low
□ Need full control over data
```

### Backup Strategy

**Three layers of backup:**

```
LAYER 1: LIVE RECOVERY
- Second browser/tab with same demo
- Know how to quickly restart

LAYER 2: BACKUP ENVIRONMENT
- Separate sandbox instance
- Pre-authenticated and ready

LAYER 3: OFFLINE BACKUP
- Screenshots of key flows
- Video recording of demo path
- Slide deck with embedded images
```

**Backup Asset Checklist:**

| Asset | Location | Format |
|-------|----------|--------|
| Screenshot set | Desktop folder | PNG |
| Demo video | Desktop + cloud | MP4 |
| Presentation backup | Desktop | PDF |
| Environment URL backup | Notes | Text |
| IT contact | Phone | Number |

### Remote Demo Technical Setup

**Video Conferencing Checklist:**

```
VISUAL
□ Lighting on face (not behind)
□ Camera at eye level
□ Background professional or virtual
□ Dressed appropriately (full outfit)

AUDIO
□ Good microphone (not laptop mic)
□ Headphones (no echo)
□ Quiet environment
□ Backup phone dial-in ready

SCREEN SHARING
□ Know how to share specific window vs full screen
□ Share only what needed
□ Resolution appropriate for viewing
□ Multiple monitors configured correctly
```

**Screen Resolution Guidance:**

| Your Resolution | Share As | Why |
|-----------------|----------|-----|
| 4K/5K | 1920x1080 | Too small for viewers otherwise |
| 1440p | 1920x1080 | Optimal for most viewers |
| 1080p | Native | Already optimal |
| Laptop | 125-150% zoom | Ensure readability |

### The Demo Dry Run

**Mandatory dry run elements:**

```
TIMING
□ Complete demo fits in allotted time
□ Identify sections that run long
□ Know what to cut if needed

FLOW
□ Transitions are smooth
□ Navigation is efficient
□ No dead ends or confusion

TECHNICAL
□ Every click works
□ Every screen loads
□ Every integration functions

CONTENT
□ Data looks correct
□ Messaging is sharp
□ Objection responses ready
```

### Environment Recovery Protocols

**Scenario: Page won't load**
```
1. Try refresh (once)
2. Open backup tab
3. If still failing, switch to backup environment
4. If all else fails, switch to screenshots/video
5. Narrate: "Let me show you this another way..."
```

**Scenario: Feature errors**
```
1. Try once more with different input
2. Note the error, don't dwell
3. Switch to adjacent feature
4. Promise to follow up: "Let me get you the recording of this working correctly"
```

**Scenario: Internet drops**
```
1. Phone hotspot (pre-configured)
2. Dial in to meeting audio
3. Verbal description while reconnecting
4. Have participant share their view if possible
```

### Environment Maintenance Schedule

| Frequency | Tasks |
|-----------|-------|
| **Weekly** | Check demo data freshness, update dates |
| **Before each demo** | Full run-through, data check |
| **Monthly** | Deep clean, remove old data, refresh content |
| **After updates** | Full feature test, update screenshots |
| **Quarterly** | Review demo flow relevance, modernize |

### Anti-Patterns

- **"It usually works"** — Not testing before demo
- **Stale data** — 2-year-old timestamps
- **Test pollution** — "Test user 123" visible
- **No backup plan** — Single point of failure
- **Over-engineering** — 2 hours of prep for 15-min demo
- **Notification pop-up** — Slack messages during demo
- **Wrong account** — Personal account vs demo account
- **Assuming it works** — Not doing dry run
