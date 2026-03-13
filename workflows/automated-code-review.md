# Automated Code Review System

## When to Use This

You have multiple developers and agents writing code at volume, and human code review is becoming the bottleneck. Use this when:
- You're merging 5+ PRs per day
- Code review wait time is >1 hour
- Humans are reviewing code they're not expert in
- You want consistent, comprehensive review without review fatigue
- You need security/safety gates before code reaches main branch

## Prerequisites

- GitHub (or equivalent) with branch protection rules
- Two agent instances for parallel review lanes
- Access to architecture documentation
- Pre-commit hooks and CI/CD pipeline running
- Code review criteria well-defined

## The Problem with Traditional Review

**Traditional flow:**
1. Developer opens PR
2. Requests review from team
3. Team is busy → 1-2 hour wait
4. Reviewer tired → skims code → clicks approve
5. Developer waits for approval → switches context
6. Later: bug found in production that review missed

**Rob's observation:** "In era of AI-driven code, you can write more code than humans can review. If you expect humans to review it, they'll say they reviewed it and click approve."

The bottleneck: humans can't keep up. Solution: automate review.

## The Automated Review System

### Two Review Lanes

Every PR runs through **two independent agents** in parallel, each with access to architecture docs:

**Lane 1: DII/Security/Safety Reviewer**
- Focuses on: Data integrity, information leaks, security risks, compliance
- Asks: "Does this code violate our data handling rules? Does it expose secrets? Is access control correct?"
- Access to: Architecture docs, security policies, database schemas

**Lane 2: Code Quality/Patterns Reviewer**
- Focuses on: Code correctness, performance, maintainability, pattern consistency
- Asks: "Is this approach sound? Does it follow our patterns? Any performance issues? Will this be maintainable?"
- Access to: Architecture docs, code quality standards, performance benchmarks

**Both must pass before merge to dev. Both must pass before merge to main.**

### Gate 1: Dev Branch Gate

When PR targets `develop`:

```
Developer opens PR
    ↓
Pre-commit hooks run (linting, formatting) ← must pass
    ↓
CI tests run ← must pass
    ↓
Security reviewer agent evaluates
    ├─ Looks for security anti-patterns
    ├─ Checks access control logic
    ├─ Verifies no credential leaks
    └─ Reports issues (fails review if found)
    ↓
Quality reviewer agent evaluates
    ├─ Checks architecture alignment
    ├─ Looks for code smells
    ├─ Verifies performance standards
    └─ Reports issues (fails review if found)
    ↓
If both pass: auto-approve, ready to merge to dev
If either fails: block, request changes
```

### Gate 2: Main Branch Gate

When PR targets `main`:

Same reviewers, but higher bar. Security reviewer also checks:
- Backwards compatibility
- Data migration safety
- Rollback plan feasibility

## Setting Up Review Agents

### Security Reviewer Setup

```yaml
name: "Security Reviewer"
model: "claude-opus-4.6"

system_prompt: |
  You are a security-focused code reviewer. Your job is to identify security,
  privacy, and data integrity issues in code changes.

  When reviewing code:
  1. Check for SQL injection vulnerabilities
  2. Verify all user input is validated
  3. Ensure auth/permission checks are in place
  4. Look for hardcoded credentials or secrets
  5. Check for information leaks (logs exposing sensitive data)
  6. Verify access control (user can only see their own data)
  7. Look for CORS/CSRF issues
  8. Verify encryption where required
  9. Check for rate limiting on sensitive endpoints
  10. Verify audit logging for compliance-critical actions

  Return structured review:
  - PASS/FAIL overall
  - List of issues (if any) with severity and location
  - Specific code lines to change
  - Suggested fixes

context_files:
  - docs/architecture.md
  - docs/security-policies.md
  - docs/data-classification.md
  - schema.sql (database structure)
```

### Quality Reviewer Setup

```yaml
name: "Quality Reviewer"
model: "claude-opus-4.6"

system_prompt: |
  You are a code quality reviewer. Your job is to identify maintainability,
  performance, and architectural issues.

  When reviewing code:
  1. Does this follow our established patterns?
  2. Are there any obvious bugs or logic errors?
  3. Is error handling adequate?
  4. Are there any N+1 queries or performance issues?
  5. Is the code testable? Are tests included?
  6. Does the code handle edge cases?
  7. Are function signatures clear?
  8. Is the code DRY or are there duplicates?
  9. Does this follow our naming conventions?
  10. Are there any security assumptions I should check?

  Return structured review:
  - PASS/FAIL overall
  - List of issues (if any) with severity and location
  - Specific code lines to change
  - Suggested improvements (optional if PASS)

context_files:
  - docs/architecture.md
  - docs/code-standards.md
  - docs/performance-targets.md
  - src/patterns/ (example code showing patterns)
```

## GitHub Actions Workflow

```yaml
name: Automated Review

on:
  pull_request:
    branches: [develop, main]

jobs:
  security-review:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
        with:
          fetch-depth: 0

      - name: Get changed files
        id: changed-files
        uses: tj-actions/changed-files@v41

      - name: Run security review agent
        env:
          CLAUDE_API_KEY: ${{ secrets.CLAUDE_API_KEY }}
          PR_NUMBER: ${{ github.event.number }}
          CHANGED_FILES: ${{ steps.changed-files.outputs.all_changed_files }}
          TARGET_BRANCH: ${{ github.base_ref }}
        run: |
          node scripts/review-agent.js --lane security

      - name: Comment review result
        if: always()
        uses: actions/github-script@v6
        with:
          script: |
            const fs = require('fs');
            const review = JSON.parse(fs.readFileSync('review-result.json'));
            github.rest.issues.createComment({
              issue_number: context.issue.number,
              owner: context.repo.owner,
              repo: context.repo.repo,
              body: review.comment
            });

      - name: Fail if review failed
        if: failure()
        run: exit 1

  quality-review:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
        with:
          fetch-depth: 0

      - name: Get changed files
        id: changed-files
        uses: tj-actions/changed-files@v41

      - name: Run quality review agent
        env:
          CLAUDE_API_KEY: ${{ secrets.CLAUDE_API_KEY }}
          PR_NUMBER: ${{ github.event.number }}
          CHANGED_FILES: ${{ steps.changed-files.outputs.all_changed_files }}
          TARGET_BRANCH: ${{ github.base_ref }}
        run: |
          node scripts/review-agent.js --lane quality

      - name: Comment review result
        if: always()
        uses: actions/github-script@v6
        with:
          script: |
            const fs = require('fs');
            const review = JSON.parse(fs.readFileSync('review-result.json'));
            github.rest.issues.createComment({
              issue_number: context.issue.number,
              owner: context.repo.owner,
              repo: context.repo.repo,
              body: review.comment
            });

      - name: Fail if review failed
        if: failure()
        run: exit 1

  require-approvals:
    needs: [security-review, quality-review]
    if: always()
    runs-on: ubuntu-latest
    steps:
      - name: Check review status
        if: needs.security-review.result != 'success' || needs.quality-review.result != 'success'
        run: |
          echo "Security review: ${{ needs.security-review.result }}"
          echo "Quality review: ${{ needs.quality-review.result }}"
          exit 1
```

## Review Request Format

When code is ready for review, the agent receives:

```
Code Review Request

PR: #142 "Add invoice filtering"
Target branch: develop
Author: alice

Changed files:
- src/services/InvoiceService.ts (120 lines)
- src/routes/invoice.ts (45 lines)
- src/components/InvoiceFilter.tsx (85 lines)
- tests/invoices.test.ts (95 lines)

Commit messages:
- feat: add invoice filtering by date range
- feat: add API endpoint for filtered queries
- test: add comprehensive filter tests

Review criteria:
1. All user input is validated
2. Database queries are parameterized
3. Error handling is complete
4. Tests have 90%+ coverage
5. Code follows established patterns

Security reviewer: Does this change violate security policies?
Quality reviewer: Is this code maintainable and correct?
```

Agent returns:

```json
{
  "overall": "PASS",
  "lane": "security",
  "issues": [],
  "suggestions": [
    "Consider adding rate limiting to filter endpoint (high volume possible)"
  ],
  "summary": "No security concerns. Well-structured input validation."
}
```

## Routing High-Value Decisions to Humans

**Key principle from Rob:** "Route only high-value decisions to human experts."

Don't send:
- "Is this 4000 lines of code correct?" → human misses issues, clicks approve
- All 50 files in refactor → human gets overwhelmed

Instead:
- "Did we miss any security implications?" → human applies expertise
- "Is our caching strategy sound?" → human evaluates trade-offs
- "Should we deprecate this API or refactor?" → human decides trade-off

**Example: Strategic decision gate**

```yaml
strategic-decisions:
  - name: "Database normalization refactor"
    route_to: ["database_expert", "data_architect"]
    question: |
      We're refactoring invoice storage. Is moving from denormalized
      (fast reads, slow writes) to normalized (slow reads, fast writes)
      the right trade-off for our access patterns?
    decision_time: "async, next day OK"

  - name: "Authentication strategy"
    route_to: ["security_lead"]
    question: |
      Should we migrate from JWT to session-based auth?
      Impacts: token size, refresh complexity, server state.
    decision_time: "sync, needs discussion"
```

Agents handle 95% of review volume. Humans handle 5% of high-value decisions.

## Measuring Reviewer Effectiveness

Track metrics for both automated reviewers:

```
Security Reviewer:
- Issues caught in review: 12 per week
- Issues found later in testing: 0 per week
- Issues found in production: 0 per month
- False positives: 1 per month
→ Effectiveness: High. Keep as-is.

Quality Reviewer:
- Performance issues caught: 3 per week
- Maintainability issues caught: 8 per week
- Issues found later in testing: 2 per week
- False positives: 4 per month
→ Effectiveness: Good. Reduce false positives (tune rules).
```

Weekly team sync: Review the metrics, adjust review criteria if needed.

## Responsibility Model

**Critical:** You own the code your AI writes.

- If your agent's code causes a production issue, that's your responsibility
- You can't say "the agent wrote it, not me"
- You can use agents to improve velocity, but not to abdicate responsibility

**Rob:** "Your job is not to build the product. Your job is to build the team that builds the product."

Your job is to:
1. Set up review criteria that catch real issues
2. Monitor reviewer effectiveness
3. Route decisions to right expertise
4. Own the code quality

## Weekly Demo & Review

Every Friday: team demos what changed in the week.

**Process:**
1. Automated reviewers generate changelog
2. Team watches demos of new features
3. Team provides feedback:
   - "That feature needs better error handling"
   - "That design doesn't match our standards"
   - "That performance is too slow"
4. Feedback loops back to coding agents/developers

**Why it works:** Feedback happens early (end of week, not in production). Issues caught by humans reviewing the output, not code reviewing the code.

## Tips & Gotchas

**Tip:** Start with one lane (security) before adding quality lane. Simpler to debug.

**Gotcha:** Reviewers need context to be useful. Bad context = bad reviews. Invest in documentation.

**Tip:** Review criteria should be testable. "Write clear code" is vague. "Add JSDoc for all public functions" is testable.

**Gotcha:** False positives will make developers ignore reviews. Keep them low.

**Tip:** Measure reviewer effectiveness quarterly. If a rule never catches issues, remove it.

**Gotcha:** Don't use this as a replacement for human code review. Use it to augment human review. Route high-value decisions to humans.

**Tip:** Store all reviews as artifacts. They're useful for onboarding and policy enforcement.

## When NOT to Use This

- Very small team (<5 developers) where reviews are quick
- Brand new codebase with unclear patterns
- Highly experimental/prototype work
