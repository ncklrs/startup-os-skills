# Logging Best Practices Rules

## Sections

### Architecture
Core architectural patterns for production logging.
- `architecture-wide-events.md` - The wide event pattern
- `architecture-event-lifecycle.md` - Building events through request lifecycle

### Field Design
What to include in your events.
- `fields-high-cardinality.md` - Embrace high-cardinality fields
- `fields-required-context.md` - Essential fields for every event
- `fields-business-context.md` - Capturing business-relevant data

### Sampling
Smart sampling strategies.
- `sampling-tail-sampling.md` - Sample after completion, not before
- `sampling-always-keep.md` - What to never sample away

### Anti-Patterns
Common mistakes to avoid.
- `antipattern-scattered-logs.md` - Stop scattering log statements
- `antipattern-string-search.md` - Design for queries, not grep
- `antipattern-otel-silver-bullet.md` - OTel is delivery, not strategy
