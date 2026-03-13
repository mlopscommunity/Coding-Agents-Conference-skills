---
name: validation-runner
description: Use to comprehensively validate code quality and correctness in a separate context from the coding agent. Catches issues that biased validation would miss, ensures linting, tests, and assumptions are valid before merge.
---

# Validation Runner

## Overview

The Validation Runner Skill performs comprehensive validation in a **separate context** from the coding agent. This is critical because if an agent makes false assumptions during coding, it will bake those assumptions into its validation. By running validation as a sub-agent with fresh context, you catch issues that the coding agent missed and prevent flawed implementations from being considered "complete."

**Core principle:** Fresh validation context catches assumption-based bugs. If the coder made a false assumption, it contaminates their own validation. You need independent verification.

**Dependency:** Claude Code CLI with test infrastructure, linting tools, and the ability to run code.

## When to Use

- After each coding session: Before merging code to main
- After parallelized agent work: Before merging multiple agents' code
- Before deployment: Final validation before production
- When you're uncertain about code quality: Get an independent assessment
- For critical systems: MLOps pipelines, data processing, ML models where bugs are expensive

## When NOT to Use

- During live pairing or rapid iteration (too slow)
- For trivial changes (typo fixes, comments, obvious improvements)
- When you trust the coding agent's validation completely (you shouldn't)

## Common Mistakes

| Mistake | Why it's wrong |
|---------|---------------|
| Skipping validation because "code looks good" | You can't see issues visually. Validation tools find real bugs. |
| Assuming the coding agent's validation is sufficient | If the agent made assumptions, it validated the wrong thing. Fresh context is essential. |
| Not running tests because "we did linting" | Linting catches style issues. Tests catch logic bugs. You need both. |
| Ignoring coverage drops | If coverage dropped, code is untested. Untested code breaks in production. |
| Treating all test failures as "probably environmental" | Test failures are real. Investigate them. |
| Skipping custom pattern checks | Pattern checks catch domain-specific issues linters miss. They're often more valuable than linting. |

## The Validation Process

### Step 1: Gather Validation Scope

Understand what we're validating:
- What code was changed? (files, lines of changes)
- What's the scope? (new feature, bugfix, refactor?)
- What systems does it touch?
- Are there any known tricky areas?
- What's the risk level? (critical, high, medium, low?)

### Step 2: Environment Setup

Set up the validation environment:

```bash
# Install dependencies (if needed)
npm install  # or pip install -r requirements.txt, etc.

# Set up test database (if needed)
# Load test fixtures
# Configure test environment

# Show what we're validating
git diff HEAD~1  # or show changed files
```

### Step 3: Run Linting

Execute all linting checks:

**JavaScript/TypeScript**:
```bash
npm run lint
# or
npx eslint . --fix --report-unused-disable-directives
# or
npx biome check .
```

**Python**:
```bash
pylint src/ --fail-under=8.0
flake8 src/
black --check src/
mypy src/
```

**Go**:
```bash
go vet ./...
golint ./...
go fmt ./...
```

**General**:
```bash
# Check for trailing whitespace, CRLF endings, etc.
# Check for commented-out code
# Check for debug prints (console.log, print(), println!)
# Check for TODOs/FIXMEs
```

**Output format**:
```
## Linting Results
✓ PASSED: ESLint (0 violations)
✓ PASSED: Black formatting
✗ FAILED: TypeScript strict null checks
  - Line 45: Variable 'user' could be undefined
  - Line 67: Cannot assign 'string' to 'number'

Custom linting checks:
✓ No console.log() in production code
✓ No commented-out code blocks
✗ WARNING: 3 TODO comments (review if intentional)
```

### Step 4: Run Unit Tests

Execute the test suite:

```bash
# Run all tests
npm test  # or pytest, go test, etc.

# Capture output:
# - Total tests run
# - Tests passed
# - Tests failed
# - Test coverage percentage
# - Coverage gaps
```

**Output format**:
```
## Unit Test Results
Total tests: 342
✓ PASSED: 340
✗ FAILED: 2

Failed tests:
  - src/models/user.test.ts: "User should not allow negative age"
  - src/api/handlers.test.ts: "GET /users/{id} should return 404 for missing user"

Coverage summary:
  Statements: 87.3% (good, was 85%)
  Branches: 72.1% (ok, watch for untested error paths)
  Functions: 91.2% (good)
  Lines: 88.4% (good)

Coverage gaps (>5% uncovered):
  - src/error_handling/retry_logic.ts (coverage: 34%)
  - src/admin/cleanup_service.ts (coverage: 21%)
```

If coverage decreased significantly, flag it.

### Step 5: Custom Pattern Checks

Run project-specific validation scripts. Create checks for patterns relevant to your codebase.

**Examples for MLOps**:
```bash
# Check model artifact versioning
find models/ -name "*.pkl" -o -name "*.joblib" | \
  while read f; do
    # Ensure artifacts have metadata
    [ -f "${f}.metadata.json" ] || echo "Missing metadata: $f"
  done

# Check training data assumptions
grep -r "assume_categorical\|drop_duplicates\|fillna" src/preprocessing/ | \
  grep -v "tested" | \
  while read line; do echo "Review assumption: $line"; done

# Check that model config changes are documented
if git diff HEAD src/config.yaml | grep -q "model:"; then
  [ -s CHANGELOG.md ] || echo "WARNING: Model config changed but no CHANGELOG entry"
fi
```

**Examples for general code**:
```bash
# No hardcoded credentials
grep -r "password\|api_key\|secret" src/ | \
  grep -v "^Binary" | \
  grep -v "\.env\|\.example" | \
  grep -v "test_\|TEST_" | \
  while read line; do echo "Potential hardcoded credential: $line"; done

# Database queries use parameterized queries
grep -r "SELECT.*FROM" src/ | \
  grep -E "f\"|\.format\(%s\)|'\s*\+\s*" | \
  while read line; do echo "Check for SQL injection risk: $line"; done

# No synchronous file I/O in async contexts
grep -r "fs\.readFileSync\|open.*read\(" src/ | \
  grep -v "test\|spec" | \
  while read line; do echo "Potential blocking I/O: $line"; done
```

**Output format**:
```
## Custom Pattern Checks
✓ PASSED: No hardcoded credentials
✓ PASSED: All SQL queries use parameterized statements
✗ FAILED: Blocking file I/O in async function
  - Line 234 of src/data_loader.py: open() blocks event loop
  - Review: Consider using aiofiles
```

### Step 6: UI/Screenshot Validation (if applicable)

If the code includes UI changes:

```bash
# Generate screenshots of key user flows
npm run screenshot:login
npm run screenshot:dashboard
npm run screenshot:settings
# or use Playwright/Puppeteer to generate
```

Validate:
- Components render without errors
- Layout is correct (no overlapping, proper spacing)
- Text is readable (no cutoff, proper colors)
- Responsive design looks good (mobile, tablet, desktop views)
- Visual regressions compared to previous version

**Output format**:
```
## UI Validation
✓ Login flow: Renders correctly
✓ Dashboard: All widgets load
✗ Settings page: Form labels misaligned on mobile
  - Screenshot: validation_failures/settings_mobile.png
  - Issue: Label text overlaps input fields

Visual regressions:
  - Dashboard card spacing increased by 2px (intentional? check design)
```

### Step 7: Run E2E Tests (if available)

If project has E2E tests:

```bash
# Run Playwright, Cypress, or other E2E framework
npx playwright test
# or
npm run e2e

# Capture:
# - Total scenarios run
# - Passed/failed
# - Any flaky tests
# - Error messages
```

**Output format**:
```
## E2E Test Results
Total scenarios: 24
✓ PASSED: 22
✗ FAILED: 2
⚠ FLAKY: 1 (passed on retry)

Failed scenarios:
  - "User can upload CSV file and see results" (connection timeout)
  - "Admin can deactivate user account" (permission denied, may be test data issue)

Flaky test:
  - "Model training completes in time limit" (sometimes slow CI runner)
```

### Step 8: Analyze Relevant Logs

Check for error patterns:

```bash
# Application logs (if running)
tail -100 logs/application.log | grep -i "error\|exception\|warning"

# Test output for warnings
# Build output for deprecation warnings
# Runtime warnings from linters
```

**Output format**:
```
## Log Analysis
Warnings found:
  - DeprecationWarning: use_param_X is deprecated (4 occurrences)
  - TypeError in error handler (review line 342)
  - Uncaught promise rejection in data fetch (review async handling)

Recommendations:
  - Replace deprecated function calls
  - Review error handler type safety
  - Ensure all promises are caught
```

### Step 9: Compile Validation Report

Create a comprehensive summary:

```
# Validation Report

**Date**: [today]
**Code scope**: [what was validated]
**Risk level**: [low/medium/high/critical]

## Summary
✓ [X] PASSED all critical checks
✗ [Y] FAILED [N] check(s), [M] warning(s)

## Results by Category

### Linting
Status: [PASS/FAIL]
- [list major issues or "no issues found"]
- Recommendations: [if any]

### Unit Tests
Status: [PASS/FAIL]
Total: 342 | Passed: 340 | Failed: 2
Coverage: 87.3% (was 85.1%) ✓ Improved
Failed tests:
- [test name]: [brief issue]
- [test name]: [brief issue]

### Custom Patterns
Status: [PASS/FAIL]
- [pattern check]: [result]
- Recommendations: [if any]

### UI Validation (if applicable)
Status: [PASS/FAIL]
- Visual regression: [status]
- Responsive design: [status]
- Issues: [list or "none"]

### E2E Tests (if applicable)
Status: [PASS/FAIL]
Total: 24 | Passed: 22 | Failed: 2
- Failed scenario: [name and reason]
- Flaky test detected: [if any]

## Issues Requiring Attention

### Critical (blocks deployment)
- [ ] [Issue 1]: [description] - FIX REQUIRED before merge
- [ ] [Issue 2]: [description] - FIX REQUIRED before merge

### High (should fix)
- [ ] [Issue 1]: [description] - Should fix before merge
- [ ] [Issue 2]: [description] - Should fix before merge

### Medium (nice to fix)
- [ ] [Issue 1]: [description] - Consider fixing
- [ ] [Issue 2]: [description] - Consider fixing

### Low (informational)
- [Note 1]: [description]
- [Note 2]: [description]

## Validation Confidence

Based on:
- Code review coverage: [good/adequate/incomplete]
- Test coverage adequacy: [good/adequate/incomplete]
- Known edge cases tested: [yes/no]
- Integration with other systems checked: [yes/no/N.A.]

Overall assessment: [The code is ready for merge / Recommend fixes before merge / Code needs significant work]

## Next Steps

If PASS:
- [ ] Approve for merge
- [ ] Ready for deployment (or further testing)

If FAIL:
- [ ] Return to coding agent with specific issues to fix
- [ ] Re-run validation after fixes
```

### Step 10: Flag for Human Review

If you encounter issues that require human judgment:

```
## Requires Human Review

### Design Decision Question
Issue: [description]
Question: Should we [option A] or [option B]?
Context: [relevant info]
→ Waiting for human decision

### Breaking Change Warning
Change: [description]
Impact: [what breaks]
Migration path: [is there one?]
→ Needs approval before proceeding

### Known Limitation
Situation: [description]
Why: [reason]
Workaround: [if available]
→ Document as known limitation or fix?
```

## Special Cases

### If Validation Fails Unexpectedly
- Don't blame the coding agent
- Report what failed, why, and what concrete fix would help
- Provide specific error messages and line numbers
- Consider: Is this a test infrastructure issue, or a real code issue?

### If You Detect Invalid Assumptions
Example: Coding agent assumed database table X exists, but it doesn't
- Report this clearly: "Code assumes [assumption], but [reality]"
- Provide evidence: show where code makes assumption
- Suggest fix: "Either add migration to create table X, or change code to use table Y"

### If Coverage Drops Significantly
- Identify what's uncovered
- Ask: Is this intentional (adding code that doesn't need testing) or a gap?
- High-risk, uncovered code (error handling, security) should be flagged

## Configuration Notes

### Project-Specific Setup

1. **Linting tools**: Specify your stack:
   ```
   JavaScript/TypeScript: ESLint + Prettier (or Biome)
   Python: pylint + flake8 + mypy + black
   Go: gofmt + vet + golangci-lint
   Custom: [add your tools]
   ```

2. **Test command**: Update validation:
   ```bash
   # Your project's test command
   npm test
   # or
   pytest --cov=src --cov-report=html
   # or
   cargo test
   ```

3. **Custom patterns**: Add checks relevant to your project:
   ```bash
   # MLOps: Check model artifact versions
   # Data pipeline: Validate data schema transformations
   # Security: Check for credential exposure
   # Performance: Check for N+1 queries
   ```

4. **Coverage thresholds**: Set acceptable coverage:
   ```
   Minimum coverage: 80%
   Critical paths: must be 95%+
   New code: should increase or maintain coverage
   ```

5. **E2E test configuration**: If using Playwright/Cypress:
   ```
   Timeout: [your setting]
   Retry failed tests: [yes/no]
   Screenshot on failure: [yes/no]
   ```

## How to Invoke

Create a separate validation session (do NOT run this in the same session as coding):

```
/validation-runner

[Paste or describe the code that was changed]
```

Or after coding work completes:

```
Use the validation-runner skill to verify the code quality.
[Provide files changed or commit SHA]
```

## Tips from Practitioners

**When to run this**: After the coding agent finishes, before merging. Never skip validation.

**Fresh context is critical**: The validator should NOT know what the coder was thinking. Fresh eyes catch assumptions.

**Test flakiness**: If a test fails inconsistently, that's a real problem. Flag it and investigate. Don't ignore "it sometimes passes."

**Coverage gaps matter**: Uncovered error handling and edge case code is high risk. Ask: should this be tested, or is it safe to leave untested?

**Common validation mistakes**:
- Skipping unit tests because "we did E2E testing"
- Not checking coverage reports carefully
- Ignoring deprecation warnings
- Not validating assumptions (file paths, config, external service availability)

**Performance validation**: If code touches data, ML models, or large datasets:
- Benchmark performance before and after
- Check for N+1 query patterns
- Verify model inference performance
- Check for memory leaks in long-running jobs

**Pro tip**: Save detailed validation reports. When bugs appear in production, review the validation report. You'll often find "we could have caught this."

**Red flags that demand investigation**:
- Test coverage decreases by >5%
- Linting violations that can't be auto-fixed
- E2E tests that are flaky
- Unit tests that timeout
- Custom pattern checks finding issues
- Log analysis showing error patterns

## Key Principles

1. **Fresh context catches assumption bugs.** If the coder made assumptions, validation in the same context validates the wrong thing.
2. **Every check serves a purpose.** Linting catches style. Tests catch logic. Pattern checks catch domain-specific issues. Coverage catches untested paths.
3. **Failures are data.** Don't ignore or work around test failures. They tell you what's broken.
4. **Assumptions are risks.** Flag them and verify them. Code that assumes file paths, config existence, or service availability will break in different environments.
5. **Coverage matters.** Untested code is time bombs. High-risk code (error handling, security) must be tested.

## Attribution

Based on techniques from the Coding Agents Lunch & Learn Series. Rob Ennals (Anthropic) and Rahul contributed the "Punch It" skill concept: "Validation must run in a fresh context. If the coding agent made assumptions, those same assumptions will be baked into the validation. You need independent verification."
