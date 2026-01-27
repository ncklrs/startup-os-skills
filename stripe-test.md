---
description: Run automated Stripe payment testing against staging environment
user-invocable: true
arguments:
  - name: url
    description: Base URL to test (e.g., https://staging.example.com)
    required: false
  - name: product
    description: Product/checkout path (e.g., /en/checkout?sku=ABC123)
    required: false
  - name: sequence
    description: Run a predefined test sequence (smoke, full, us-all, cards-all, etc.)
    required: false
  - name: scenario
    description: Specific scenario to run (e.g., US-CARD-VISA)
    required: false
  - name: country
    description: Filter by country code (US, GB, AU, CA)
    required: false
  - name: payment
    description: Filter by payment method (card, affirm, us_bank_account)
    required: false
  - name: verbose
    description: Enable verbose logging
    required: false
  - name: screenshots
    description: Capture screenshots during tests
    required: false
---

# Stripe Payment Testing Automation

Automated end-to-end testing of Stripe payment flows on the TonyRobbins.com staging environment.

## Overview

This skill runs complete purchase flows through the staging checkout, testing:
- Multiple payment methods (card, Affirm, US bank account)
- International customers (US, UK, Australia, Canada)
- Tax calculations (VAT, GST)
- Error handling (declined cards, 3D Secure)

## Usage

### Configure URL and Product (Primary Options)
```bash
# Test a specific URL with smoke test
bun run scripts/stripe-testing/src/index.ts \
  --url https://staging.example.com \
  --sequence smoke

# Test a specific product/checkout page
bun run scripts/stripe-testing/src/index.ts \
  --url https://staging.example.com \
  --product "/en/checkout?sku=PROD-123" \
  --sequence us-all

# Override URL for all scenarios in a sequence
bun run scripts/stripe-testing/src/index.ts \
  --url https://my-feature-branch.vercel.app \
  --sequence pre-release \
  --verbose
```

### Run a test sequence (recommended)
```bash
# Quick smoke test
bun run scripts/stripe-testing/src/index.ts --sequence smoke

# All US payment methods in order
bun run scripts/stripe-testing/src/index.ts --sequence us-all

# Full regression suite
bun run scripts/stripe-testing/src/index.ts --sequence full --verbose

# List all available sequences
bun run scripts/stripe-testing/src/index.ts --list-sequences
```

### Run all tests
```bash
bun run scripts/stripe-testing/src/index.ts
```

### Run specific scenario
```bash
bun run scripts/stripe-testing/src/index.ts --scenario US-CARD-VISA
```

### Filter by country
```bash
bun run scripts/stripe-testing/src/index.ts --country US
bun run scripts/stripe-testing/src/index.ts --country GB
```

### Filter by payment method
```bash
bun run scripts/stripe-testing/src/index.ts --payment-method card
bun run scripts/stripe-testing/src/index.ts --payment-method affirm
```

### With screenshots and verbose logging
```bash
bun run scripts/stripe-testing/src/index.ts --country GB --verbose --screenshots
```

## Available Scenarios

| ID | Description | Payment Method | Country |
|----|-------------|----------------|---------|
| `US-CARD-VISA` | US customer with Visa card | Card | US |
| `US-CARD-MC` | US customer with Mastercard | Card | US |
| `US-CARD-AMEX` | US customer with Amex | Card | US |
| `US-AFFIRM` | US customer with Affirm BNPL | Affirm | US |
| `US-BANK` | US customer with ACH bank transfer | US Bank | US |
| `UK-CARD` | UK customer with VAT (20%) | Card | GB |
| `AU-CARD` | Australian customer with GST (10%) | Card | AU |
| `CA-CARD` | Canadian customer | Card | CA |
| `DECLINE-CARD` | Test declined card error handling | Card | US |
| `3DS-CARD` | Test 3D Secure authentication | Card | US |

## Available Sequences

Sequences run multiple scenarios in a defined order, with optional delays between tests. Use `--list-sequences` to see all options.

| ID | Name | Scenarios | Use Case |
|----|------|-----------|----------|
| `smoke` | Smoke Test | US-CARD-VISA | Quick verification (stops on failure) |
| `us-all` | US All Payment Methods | VISA → MC → AMEX → Affirm → Bank | Test all US payment options |
| `cards-all` | All Card Types | 6 card scenarios across countries | Verify card processing |
| `international-tax` | International Tax | UK-CARD → AU-CARD | Validate VAT/GST |
| `error-handling` | Error Handling | DECLINE-CARD → 3DS-CARD | Test failure paths |
| `progressive` | Progressive Complexity | VISA → UK → AU → 3DS | Build up from simple (stops on failure) |
| `full` | Full Regression | All 10 scenarios | Complete test coverage |
| `alternative-payments` | Alternative Payments | Affirm → Bank | BNPL and ACH testing |
| `pre-release` | Pre-Release Checklist | VISA → UK → DECLINE | Critical paths before release |

### Sequence Features
- **Stop on failure**: Some sequences stop at first failure (`smoke`, `progressive`, `pre-release`)
- **Delays**: Configurable delay between scenarios (prevents rate limiting)
- **Flow visualization**: See the chain of tests in output

## Output

### Console Output
- Real-time progress during test execution
- Pass/fail status for each scenario
- Summary statistics
- Recommendations for failed tests

### Markdown Report
- Saved to `reports/stripe-test-{timestamp}.md`
- Includes detailed test results
- Statistics by payment method and country
- Tax validation results
- Screenshots (if enabled)

### Screenshots
- Saved to `screenshots/` directory (if `--screenshots` flag used)
- Captures: checkout page, after submit, final result, errors

## Requirements

### Installation
```bash
# Install agent-browser CLI globally
npm install -g @anthropic-ai/agent-browser

# Install browsers
agent-browser install
```

### Environment Variables
Create a `.env` file:
```bash
STAGING_BASE_URL=https://snty-tryout-fe.tonyrobbins.com
TEST_EMAIL_DOMAIN=example.com
AGENT_BROWSER_HEADLESS=true
TEST_TIMEOUT_MS=30000
VERBOSE=false
CAPTURE_SCREENSHOTS=false
```

## Notes

### Limitations
- **Stripe iframe interaction**: agent-browser has limitations with Stripe Elements iframes. The implementation includes fallback JavaScript injection, but for production use, consider migrating to Playwright.
- **Affirm/Bank flows**: These payment methods may require additional configuration in staging.
- **Test cards**: Uses Stripe test cards (no real charges).

### Test Data
- **Email addresses**: Auto-generated test emails using pattern `test+{scenario-id}-{timestamp}@{domain}`
- **Card numbers**: Stripe test cards from official documentation
- **Addresses**: Realistic but fake addresses for each country

### Average Duration
- Single scenario: ~12-15 seconds
- Full suite (10 scenarios): ~2-3 minutes

## Troubleshooting

### agent-browser not found
```bash
npm install -g @anthropic-ai/agent-browser
agent-browser install
```

### Tests timing out
- Increase `TEST_TIMEOUT_MS` environment variable
- Check staging environment availability
- Run with `--verbose` flag to see detailed logs

### Stripe iframe errors
- This is a known limitation of agent-browser
- Consider migrating to Playwright for more reliable Stripe integration
- See `src/browser.ts` for fallback implementation

### Payment method not available
- Verify payment method is configured in staging
- Check Stripe dashboard settings
- Review checkout page configuration

## Examples

### Quick smoke test (verifies basic checkout works)
```bash
bun run scripts/stripe-testing/src/index.ts --sequence smoke
```

### Test all US payment methods in sequence
```bash
bun run scripts/stripe-testing/src/index.ts --sequence us-all --verbose
```

### Pre-release verification
```bash
bun run scripts/stripe-testing/src/index.ts --sequence pre-release --screenshots
```

### Test international tax calculations
```bash
bun run scripts/stripe-testing/src/index.ts --sequence international-tax
```

### Debug a specific failing scenario
```bash
bun run scripts/stripe-testing/src/index.ts --scenario DECLINE-CARD --verbose --screenshots
```

### Full regression test
```bash
bun run scripts/stripe-testing/src/index.ts --sequence full --screenshots
```

### Progressive testing (stops on first failure)
```bash
bun run scripts/stripe-testing/src/index.ts --sequence progressive --verbose
```

## Architecture

### Components
- `src/types.ts` - TypeScript type definitions
- `src/config.ts` - Test scenarios and configuration
- `src/utils.ts` - Helper functions
- `src/browser.ts` - Browser automation wrapper (agent-browser)
- `src/checkout-flow.ts` - Checkout flow automation
- `src/report-generator.ts` - Markdown report generation
- `src/index.ts` - Main orchestrator

### Test Flow
1. Initialize browser session
2. Navigate to checkout URL
3. Fill contact information
4. Fill address
5. Fill payment details
6. Verify pricing/tax
7. Submit payment
8. Handle 3DS (if required)
9. Verify result (confirmation page or error)
10. Generate report

## Future Enhancements

- **Playwright migration**: More reliable Stripe iframe interaction
- **Parallel execution**: Run multiple tests concurrently
- **API validation**: Verify Payment Intent status via Stripe API
- **Performance metrics**: Track page load times, API response times
- **Visual regression**: Compare screenshots against baseline
- **CI/CD integration**: Run automatically on PR builds
