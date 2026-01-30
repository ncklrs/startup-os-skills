---
title: Anti-Pattern - String Search Logging
impact: HIGH
tags: anti-pattern, grep, structured-logging
---

## Anti-Pattern: String Search Logging

**Impact: HIGH**

Designing logs for grep/string search treats them as character bags with no structural understanding. Design for queries, not grep.

### The Problem

```javascript
// ❌ STRING-BASED LOGGING
logger.info(`User user-123 logged in from 192.168.1.1`);
logger.info(`user_id=user-123 action=login ip=192.168.1.1`);
logger.info(`[LOGIN] User: user-123, IP: 192.168.1.1`);
logger.info(`{"userId": "user-123", "action": "login"}`); // JSON string, not object!

// Same entity, 4 different formats. Grep hell:
// grep "user-123" | grep "user_id=user-123" | grep "User: user-123" | grep '"userId": "user-123"'
```

### Why String Search Fails

| Issue | Impact |
|-------|--------|
| **Inconsistent formats** | Same user ID appears in 5 different patterns |
| **No structure** | Can't query `WHERE user_id = 'x'` |
| **Regex complexity** | Extracting values requires fragile regex |
| **No aggregation** | Can't `GROUP BY` or `COUNT` efficiently |
| **No type safety** | Everything is a string |

### The Solution: Structured Fields

```javascript
// ✅ STRUCTURED LOGGING
logger.info({
  event_type: 'user_login',
  user: {
    id: 'user-123',
    email_domain: 'company.com',
    tier: 'enterprise'
  },
  client: {
    ip: '192.168.1.1',
    user_agent: 'Mozilla/5.0...',
    geo_country: 'US'
  },
  auth: {
    method: 'password',
    mfa_used: true
  },
  request_id: 'req-abc123',
  timestamp: Date.now()
});
```

### Query Power

```sql
-- Structured: Simple, fast, exact
SELECT * FROM logs
WHERE user.id = 'user-123'
  AND event_type = 'user_login';

-- Aggregation enabled
SELECT
  client.geo_country,
  COUNT(*) as logins,
  COUNT(DISTINCT user.id) as unique_users
FROM logs
WHERE event_type = 'user_login'
  AND timestamp > NOW() - INTERVAL 24 HOUR
GROUP BY client.geo_country;

-- String search: Fragile, slow, incomplete
grep "user-123" logs.txt | grep -E "(login|logged in|LOGIN)"
```

### Common String-Based Anti-Patterns

```javascript
// ❌ String interpolation
logger.info(`Processing order ${orderId} for user ${userId}`);

// ❌ Key-value string format
logger.info(`order_id=${orderId} user_id=${userId} status=processing`);

// ❌ JSON as string (not parsed)
logger.info(JSON.stringify({ orderId, userId, status: 'processing' }));

// ❌ Inconsistent separators
logger.info(`Order: ${orderId}, User: ${userId}, Status: processing`);
logger.info(`[Order ${orderId}] [User ${userId}] processing`);
```

### Correct Patterns

```javascript
// ✅ Structured object
logger.info({
  event_type: 'order_processing',
  order: { id: orderId, status: 'processing' },
  user: { id: userId },
  request_id: requestId
});

// ✅ With proper logger configuration
const logger = pino({
  formatters: {
    level: (label) => ({ level: label })
  }
});
```

### Logger Configuration

Ensure your logger outputs proper JSON:

```javascript
// pino (recommended)
import pino from 'pino';
const logger = pino({ level: 'info' });

// winston
import winston from 'winston';
const logger = winston.createLogger({
  format: winston.format.json(),
  transports: [new winston.transports.Console()]
});

// bunyan
import bunyan from 'bunyan';
const logger = bunyan.createLogger({ name: 'app' });
```

### Checklist

- [ ] No string interpolation in log messages
- [ ] All context passed as structured object
- [ ] Logger configured to output JSON
- [ ] Consistent field names across codebase
- [ ] Can query any field with `WHERE field.subfield = 'value'`
- [ ] No regex required to extract values
