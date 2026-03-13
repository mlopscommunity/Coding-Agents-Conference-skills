# Validation Sub-Agent Pipeline

## When to Use This

You have agents doing extensive work (full features, large refactors) and need quality assurance that isn't influenced by the original agent's assumptions. Use this pattern when:
- Coding agent will blow its context window during work
- You need validation that isn't biased by the coder's assumptions
- You want higher test coverage than you'd ask of humans
- You're running multiple parallel coding agents
- Code complexity demands fresh-eyes review

## Prerequisites

- Multiple agent instances available (1 coder + N validators)
- Testing infrastructure: Jest/Vitest, Playwright, logging system
- Custom linting rules defined for your domain
- Ability to spin up parallel agents for validation
- Git setup for clean branching

## The Core Problem

**Why validation in the same context window fails:**

When a coding agent makes a false assumption early (e.g., "field X is always a string"), it bakes that assumption into:
- Implementation
- Type definitions
- Business logic
- Tests

Then it validates against its own tests, which encode the same false assumption.

**Result:** Bug reaches production. Fresh eyes would have caught it immediately.

**Rob's principle:** "Never run validation in the same context window as the coding agent."

## The Validation Pipeline

### Stage 1: Custom Linting Rules

**What it is:** Scripts beyond ESLint/BiomeJS that catch domain-specific patterns.

**Examples:**

```javascript
// Rule: All database queries must use parameterized statements
// (catches manual string concatenation)
rule: "no-sql-string-concat"
checks: for patterns like query = "SELECT * FROM users WHERE id = " + userId

// Rule: Redux actions must dispatch with payload type validation
// (catches missing Pydantic-style validation in action payloads)
rule: "redux-payload-shape"
checks: Redux dispatches include __schema validation

// Rule: User-facing text must be i18n'd
// (catches hardcoded English strings)
rule: "require-i18n-strings"
checks: User-facing strings wrapped in t() helper

// Rule: No floating point currency calculations
// (catches penny-rounding bugs)
rule: "no-float-currency"
checks: Currency stored as integers (cents), not floats
```

**Setup:**

```javascript
// custom-linting-rules.js
module.exports = {
  rules: {
    'no-sql-string-concat': {
      create(context) {
        return {
          BinaryExpression(node) {
            if (node.operator === '+') {
              if (isSQLQuery(node.left) && !isParameterized(node.right)) {
                context.report({
                  node,
                  message: 'SQL queries must use parameterized statements'
                });
              }
            }
          }
        };
      }
    },
    // ... more rules
  }
};
```

These rules are **non-negotiable**. Code fails validation if rules fail.

### Stage 2: Unit Tests (Broader Coverage)

Dedicated test agent writes tests at higher coverage than humans would expect:

- **Target:** 90%+ coverage (agents write fast, test data is cheap)
- **Scope:** Every function, every branch, every error path
- **Technique:** Parameterized tests for combinations

**Example:**

```typescript
// Coding agent wrote: convertCurrency(amount, fromCurrency, toCurrency)
// Coverage target: 100%

describe('convertCurrency', () => {
  // Happy path
  test('converts USD to EUR', () => { ... });

  // Edges
  test('handles zero amount', () => { ... });
  test('handles same currency (return as-is)', () => { ... });
  test('handles 3+ decimal currencies (e.g., BHD)', () => { ... });
  test('handles historical exchange rates', () => { ... });

  // Errors
  test('throws on unknown source currency', () => { ... });
  test('throws on unknown target currency', () => { ... });
  test('throws on null amount', () => { ... });
  test('throws on negative amount', () => { ... });

  // Boundary conditions
  const currencies = ['USD', 'EUR', 'JPY', 'GBP', 'CHF'];
  currencies.forEach(from => {
    currencies.forEach(to => {
      test(`converts ${from} to ${to}`, () => { ... });
    });
  });
});
```

If coverage < 90%, test agent flags it. Code loops back for more coverage.

### Stage 3: Sub-Agents for Bad Pattern Detection

Dedicated agent reviews code for patterns the linter doesn't catch:

**What it checks:**

1. **Mutability issues**
   - Redux state being mutated directly
   - Shared object references causing unexpected updates
   - Arrays/objects passed by reference instead of cloned

2. **Async bugs**
   - Race conditions in state updates
   - Missing await statements
   - Unhandled promise rejections

3. **Scope/closure leaks**
   - Variables captured incorrectly in loops
   - Memory leaks from uncleared listeners
   - Stale closures holding old state

4. **Business logic validation**
   - Violates written spec
   - Inconsistent with existing code patterns
   - Handles edge cases incorrectly

**Process:**

```
Pattern agent reads code, generates checklist:

Function: processPayment()
✓ No shared state mutations
✓ All promises awaited
✓ Error handling present
✗ Missing: null check on amount before calculations
✗ Missing: log transaction ID for auditing

Issues found. Loop code back to coder.
```

### Stage 4: Screenshot & Visual Validation

For UI components: one agent generates screenshots, another validates.

**Generator agent:**
- Takes UI component
- Renders in multiple viewport sizes (mobile, tablet, desktop)
- Generates screenshots with descriptions

```
Dashboard with filter applied - light mode
Dashboard with filter applied - dark mode
Dashboard on mobile (portrait)
Dashboard on mobile (landscape)
Filter panel opened (shows field hierarchy)
Error state (no results found)
Loading state (skeleton screens)
```

**Validator agent (separate context):**
- Sees screenshots
- Doesn't see code
- Validates: does it look correct?
- Reports: colors match brand, spacing is consistent, text is readable, interactions work

**Why separate agents:**
If the coder made a visual mistake (wrong color, bad spacing), the coder might not see it in their own screenshots. Fresh eyes catch it.

### Stage 5: E2E Tests with Playwright

Agent writes comprehensive E2E tests covering user journeys:

```typescript
describe('User filters invoices', () => {
  test('User opens filter panel and filters by date range', async () => {
    const page = await browser.newPage();
    await page.goto('/dashboard');

    // User sees all invoices
    const allRows = await page.locator('[data-test="invoice-row"]').count();
    expect(allRows).toBeGreaterThan(10);

    // User clicks filter button
    await page.click('[data-test="filter-btn"]');

    // Filter panel opens
    await expect(page.locator('[data-test="filter-panel"]')).toBeVisible();

    // User enters date range
    await page.fill('[data-test="filter-from-date"]', '2024-01-01');
    await page.fill('[data-test="filter-to-date"]', '2024-03-31');

    // User applies filter
    await page.click('[data-test="filter-apply"]');

    // Page shows only filtered results
    const filtered = await page.locator('[data-test="invoice-row"]').count();
    expect(filtered).toBeLessThan(allRows);

    // Results match criteria
    const firstRowDate = await page.locator('[data-test="invoice-date"]').first().textContent();
    expect(parseDate(firstRowDate)).toBeGreaterThanOrEqual(new Date('2024-01-01'));
  });
});
```

E2E tests run against staging environment (not mocked).

### Stage 6: Sensory & Log Analysis

Agent reviews application logs and system behavior:

**Log agent checks:**
- No ERROR level logs during happy path execution
- No WARN logs that indicate edge case handling
- Performance: API response times < 100ms
- Database query efficiency: no N+1 queries
- Memory: no growth over time (leak detection)

**Process:**

```
Log agent runs feature end-to-end, captures logs:

[SUCCESS] Login endpoint responded in 45ms
[SUCCESS] Dashboard load completed in 230ms
[SUCCESS] Filter query returned 150 results in 38ms
[WARNING] Unoptimized query: Product list loaded N+1 queries (loop issue)
[ERROR] Currency conversion failed silently, returned undefined

Issues found:
- Product list: N+1 query problem
- Currency conversion: error handling missing

Code loops back to coder.
```

## The Validation Loop

```
Coder agent completes feature
                    ↓
            Linting agent runs
             Fails? Loop back ↷
             Passes? Continue
                    ↓
          Test coverage agent
             <90%? Loop back ↷
             90%+? Continue
                    ↓
         Pattern detection agent
            Issues found? Loop back ↷
            All clear? Continue
                    ↓
      Screenshot validation (UI features)
         Looks wrong? Loop back ↷
         Looks good? Continue
                    ↓
            E2E tests run
           Tests fail? Loop back ↷
           Tests pass? Continue
                    ↓
         Log analysis agent
          Issues found? Loop back ↷
          All clear? Continue
                    ↓
       Code READY FOR REVIEW
```

Each stage is independent. If Stage 2 (tests) finds issues, coder loops back. They don't re-run earlier stages.

## Why This Works

**The bug is usually obvious to fresh eyes.** The coder's context was spent building, not validating. They're tired. They made assumptions. Validation agent has:

1. Fresh context
2. Different perspective
3. Comprehensive checklists
4. No fatigue

**Parallel execution:** While coder works on Feature B, validator finishes Feature A. No context switching.

## Configuration Example

```yaml
# validation-pipeline.yaml

stages:
  - name: "Linting"
    agent: "lint-bot"
    blocking: true
    timeout: 5m
    rules:
      - custom-linting-rules.js
      - eslint-config.js

  - name: "Unit Tests"
    agent: "test-bot"
    blocking: true
    timeout: 15m
    config:
      minCoverage: 90
      coverageReporter: "lcov"

  - name: "Pattern Detection"
    agent: "pattern-bot"
    blocking: true
    timeout: 10m
    checks:
      - mutability
      - async-correctness
      - scope-leaks
      - business-logic

  - name: "Visual Validation"
    agent: "screenshot-validator"
    blocking_on: ["ui-components"]
    timeout: 10m
    viewports:
      - { width: 375, height: 667 }   # Mobile
      - { width: 768, height: 1024 }  # Tablet
      - { width: 1920, height: 1080 } # Desktop

  - name: "E2E Tests"
    agent: "e2e-bot"
    blocking: true
    timeout: 20m
    browser: "chromium"
    environment: "staging"

  - name: "Log Analysis"
    agent: "log-analyzer"
    blocking: true
    timeout: 5m
    checks:
      - error-logs
      - performance (response times)
      - database-efficiency
      - memory-leaks
```

## Tips & Gotchas

**Tip:** The more parallel agents you run, the more important validation becomes. Validation catches issues before they spread.

**Gotcha:** Validation pipelines are slow. Feature X takes 2 hours from code to validated. Plan accordingly.

**Tip:** Start with Stages 1-2 (linting + tests). Add visual validation once UI testing becomes painful. Add log analysis for performance-critical features.

**Gotcha:** Custom linting rules have false positives. Keep them strict but review them quarterly.

**Tip:** Use validation agents for code review too. They can review human code with the same checklist.

**Gotcha:** Don't skip early stages. A bug caught by linting saves hours vs catching it in logs.

## When NOT to Use This Pattern

- Single small feature (overkill)
- Feature with minimal business logic (validation overhead > benefit)
- Quick prototypes (validation delays iteration)
