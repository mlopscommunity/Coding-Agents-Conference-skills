---
name: hooks-and-enforcement
description: Use when setting up guardrails for AI coding agents to enforce quality, security, and auditability requirements that must never be bypassed, or when configuring Claude Code lifecycle hooks in settings.json.
---

# Hooks and Enforcement

## Overview

Lifecycle hooks are the mechanism for enforcing rules that an AI agent must follow without exception. While `CLAUDE.md` instructions guide behavior, they are suggestions the agent can interpret loosely or skip. Hooks are enforcement -- they run automatically at defined points in the agent's lifecycle and block progress when checks fail.

**Core principle:** Instructions in CLAUDE.md are suggestions; hooks are enforcement. Use hooks for anything that MUST happen.

**Dependency:** Claude Code with `settings.json` hook configuration. Security scanning tools (e.g., Semgrep) for code analysis hooks.

## When to Use

- When you need linting, tests, or compilation to pass before every commit
- When agent-generated code must be scanned for security vulnerabilities before shipping
- When you need an audit trail of every shell command the agent runs
- When you want automated approval of safe permission prompts to reduce friction
- When you have tests or files the agent must never modify

## When NOT to Use

- For stylistic preferences or soft guidelines (put those in CLAUDE.md)
- For checks that are slow and disruptive when run on every edit (use pre-commit instead)
- When the project has no CI/CD and no quality requirements

## Common Mistakes

| Mistake | Why it's wrong |
|---------|---------------|
| Putting critical rules only in CLAUDE.md | CLAUDE.md is advisory. The agent can misinterpret or skip instructions. Hooks enforce mechanically -- they cannot be bypassed. |
| Using per-edit hooks for slow operations like full test suites | Per-edit hooks fire constantly and destroy flow. Sid: pre-commit hooks are preferred because they are "less disruptive to flow." Reserve per-edit for fast checks only. |
| Letting the agent modify its own test files | The agent will "fix" failing tests by weakening assertions. Create immutable test files the agent cannot touch. Josh: "Create immutable tests the agent cannot modify." |
| Skipping audit logging for agent sessions | Without an audit trail you cannot debug what went wrong. Log every shell command with timestamp. Milan: "You need to know what the agent did and when." |
| Running security scans only in CI | Agent-generated code can introduce vulnerabilities locally before it ever reaches CI. Scan before commit so vulnerabilities never enter the repo. |

## Hook Types in Claude Code

Claude Code supports lifecycle hooks configured in `.claude/settings.json`. Hooks fire at specific points and can block the agent from continuing.

### Hook Configuration Format

All hooks are defined in `.claude/settings.json` under the `hooks` key:

```json
{
  "hooks": {
    "PreToolUse": [],
    "PostToolUse": [],
    "Notification": [],
    "Stop": []
  }
}
```

Each hook entry has this shape:

```json
{
  "matcher": "tool_name_or_pattern",
  "hooks": [
    {
      "type": "command",
      "command": "shell command to run"
    }
  ]
}
```

- A hook command that **exits 0** means success (allow the action).
- A hook command that **exits non-zero** means failure (block the action).
- Hook commands receive context via `STDIN` as JSON, including the tool name and input.

---

## Technique 1: Pre-Commit Quality Enforcement

Enforce linting, tests, and compilation before every commit. This is the most important hook -- it guarantees no broken code enters the repository.

### Step 1: Create the enforcement script

Write a script that runs your full quality gate:

```bash
#!/usr/bin/env bash
# .claude/hooks/pre-commit-checks.sh
set -euo pipefail

echo "Running linter..."
npm run lint 2>&1 || { echo "BLOCKED: Lint failures"; exit 1; }

echo "Running tests..."
npm run test 2>&1 || { echo "BLOCKED: Test failures"; exit 1; }

echo "Checking types..."
npx tsc --noEmit 2>&1 || { echo "BLOCKED: Type errors"; exit 1; }

echo "All checks passed."
exit 0
```

### Step 2: Configure the pre-commit hook

Wire the script to fire before any commit tool use:

```json
{
  "hooks": {
    "PreToolUse": [
      {
        "matcher": "Bash",
        "hooks": [
          {
            "type": "command",
            "command": "bash -c 'INPUT=$(cat); if echo \"$INPUT\" | grep -q \"git commit\"; then bash .claude/hooks/pre-commit-checks.sh; fi'"
          }
        ]
      }
    ]
  }
}
```

This intercepts any `Bash` tool call containing `git commit` and runs the quality gate first. If the script exits non-zero, the commit is blocked.

---

## Technique 2: Immutable Tests

Prevent the agent from modifying test files that define your acceptance criteria. The agent's job is to make the tests pass, not to change the tests.

### Step 1: Define protected file patterns

Create a hook that blocks writes to test files:

```json
{
  "hooks": {
    "PreToolUse": [
      {
        "matcher": "Edit|Write",
        "hooks": [
          {
            "type": "command",
            "command": "bash -c 'INPUT=$(cat); FILE=$(echo \"$INPUT\" | jq -r \".file_path // .filePath // empty\"); if echo \"$FILE\" | grep -qE \"(tests/acceptance/|__tests__/immutable/|*.spec.frozen.ts)\"; then echo \"BLOCKED: This test file is immutable. Make the code pass the test instead.\"; exit 1; fi'"
          }
        ]
      }
    ]
  }
}
```

### Step 2: Structure your test directories

```
tests/
  acceptance/         # Immutable -- agent cannot modify
    auth.test.ts
    checkout.test.ts
  unit/               # Agent can modify and create
    utils.test.ts
    helpers.test.ts
```

Put your critical acceptance criteria in `tests/acceptance/`. The agent can create and modify unit tests freely but cannot touch the acceptance tests that define correctness.

---

## Technique 3: Audit Trail Logging

Log every shell command the agent executes with a timestamp. Essential for debugging, security review, and understanding what the agent did during a session.

### Step 1: Create the audit logger

```bash
#!/usr/bin/env bash
# .claude/hooks/audit-log.sh
INPUT=$(cat)
TIMESTAMP=$(date -u +"%Y-%m-%dT%H:%M:%SZ")
TOOL=$(echo "$INPUT" | jq -r '.tool_name // "unknown"')
COMMAND=$(echo "$INPUT" | jq -r '.tool_input.command // .tool_input.content // "N/A"' | head -c 500)

LOG_DIR=".claude/audit"
mkdir -p "$LOG_DIR"
LOG_FILE="$LOG_DIR/$(date -u +%Y-%m-%d).jsonl"

echo "{\"timestamp\":\"$TIMESTAMP\",\"tool\":\"$TOOL\",\"command\":$(echo "$COMMAND" | jq -Rs .)}" >> "$LOG_FILE"

# Always exit 0 -- this is observational, never blocking
exit 0
```

### Step 2: Configure the audit hook

Attach it to `PostToolUse` so it fires after every tool invocation without blocking:

```json
{
  "hooks": {
    "PostToolUse": [
      {
        "matcher": "Bash|Edit|Write",
        "hooks": [
          {
            "type": "command",
            "command": "bash .claude/hooks/audit-log.sh"
          }
        ]
      }
    ]
  }
}
```

### Step 3: Gitignore the audit logs

```gitignore
# .gitignore
.claude/audit/
```

Audit logs are session artifacts. Review them when needed, but do not commit them to the repository.

---

## Technique 4: Security Scanning Before Commit

Scan agent-generated code with security tools before it enters the repository. Catches vulnerabilities, secrets, and unsafe patterns before they become part of the codebase.

### Step 1: Create the security scan script

```bash
#!/usr/bin/env bash
# .claude/hooks/security-scan.sh
set -euo pipefail

echo "Running Semgrep security scan..."
semgrep --config=auto --error --quiet . 2>&1 || {
  echo "BLOCKED: Security issues found. Review Semgrep output above."
  exit 1
}

echo "Checking for secrets..."
if command -v gitleaks &> /dev/null; then
  gitleaks detect --source=. --no-git --quiet 2>&1 || {
    echo "BLOCKED: Potential secrets detected in code."
    exit 1
  }
fi

echo "Security scan passed."
exit 0
```

### Step 2: Wire it into the pre-commit hook

Add it to the same `PreToolUse` matcher that gates commits:

```json
{
  "hooks": {
    "PreToolUse": [
      {
        "matcher": "Bash",
        "hooks": [
          {
            "type": "command",
            "command": "bash -c 'INPUT=$(cat); if echo \"$INPUT\" | grep -q \"git commit\"; then bash .claude/hooks/security-scan.sh; fi'"
          }
        ]
      }
    ]
  }
}
```

---

## Technique 5: LLM-Powered Auto-Approval

Reduce friction from permission prompts by using an LLM to auto-approve safe operations. An outer model evaluates each permission request and approves routine actions while escalating risky ones.

### Step 1: Create the approval script

```bash
#!/usr/bin/env bash
# .claude/hooks/auto-approve.sh
INPUT=$(cat)
TOOL=$(echo "$INPUT" | jq -r '.tool_name // "unknown"')
COMMAND=$(echo "$INPUT" | jq -r '.tool_input.command // empty')

# Fast-path: always approve safe read-only commands
if echo "$COMMAND" | grep -qE "^(ls|cat|head|tail|wc|find|grep|rg|git status|git log|git diff|pwd)"; then
  exit 0
fi

# Fast-path: always block destructive commands
if echo "$COMMAND" | grep -qE "(rm -rf /|sudo|chmod 777|curl.*\| bash)"; then
  echo "BLOCKED: Destructive or unsafe command detected."
  exit 1
fi

# For ambiguous commands, you could call an outer LLM here
# to classify risk level. For now, allow by default:
exit 0
```

### Step 2: Configure as a PreToolUse hook

```json
{
  "hooks": {
    "PreToolUse": [
      {
        "matcher": "Bash",
        "hooks": [
          {
            "type": "command",
            "command": "bash .claude/hooks/auto-approve.sh"
          }
        ]
      }
    ]
  }
}
```

The key insight from Yari: an outer LLM can evaluate permission requests in context and auto-approve safe ones, dramatically reducing the number of interruptions during agent sessions.

---

## Putting It All Together

A complete `.claude/settings.json` combining all techniques:

```json
{
  "hooks": {
    "PreToolUse": [
      {
        "matcher": "Bash",
        "hooks": [
          {
            "type": "command",
            "command": "bash .claude/hooks/auto-approve.sh"
          },
          {
            "type": "command",
            "command": "bash -c 'INPUT=$(cat); if echo \"$INPUT\" | grep -q \"git commit\"; then bash .claude/hooks/pre-commit-checks.sh && bash .claude/hooks/security-scan.sh; fi'"
          }
        ]
      },
      {
        "matcher": "Edit|Write",
        "hooks": [
          {
            "type": "command",
            "command": "bash -c 'INPUT=$(cat); FILE=$(echo \"$INPUT\" | jq -r \".file_path // .filePath // empty\"); if echo \"$FILE\" | grep -qE \"tests/acceptance/\"; then echo \"BLOCKED: Immutable test file.\"; exit 1; fi'"
          }
        ]
      }
    ],
    "PostToolUse": [
      {
        "matcher": "Bash|Edit|Write",
        "hooks": [
          {
            "type": "command",
            "command": "bash .claude/hooks/audit-log.sh"
          }
        ]
      }
    ]
  }
}
```

## Quick Reference

| Item | Location / Config |
|------|-------------------|
| Hook configuration | `.claude/settings.json` under `hooks` key |
| Pre-commit quality gate | `PreToolUse` matcher on `Bash`, filter for `git commit` |
| Immutable tests | `PreToolUse` matcher on `Edit\|Write`, filter by file path |
| Audit trail logs | `PostToolUse` matcher, logs to `.claude/audit/*.jsonl` |
| Security scanning | `PreToolUse` matcher on `Bash`, filter for `git commit` |
| Auto-approval | `PreToolUse` matcher on `Bash`, fast-path safe commands |
| Hook scripts directory | `.claude/hooks/` |

## Key Principles

1. **CLAUDE.md is suggestion; hooks are enforcement.** If something must happen, it must be a hook. A forgotten instruction in CLAUDE.md is a soft failure. A failing hook is a hard stop.
2. **Prefer pre-commit over per-edit hooks.** Running the full test suite on every file edit destroys flow. Gate commits instead -- the agent can iterate freely, and quality is enforced at the boundary that matters.
3. **Make tests immutable, not just instructions.** Telling the agent "don't modify tests" in CLAUDE.md is a suggestion it can ignore. A PreToolUse hook that blocks writes to `tests/acceptance/` is a wall it cannot climb.
4. **Log everything, block selectively.** Audit trail hooks should always exit 0 -- they observe, never block. Quality and security hooks should exit non-zero to block bad code.
5. **Scan before commit, not just in CI.** Agent-generated vulnerabilities caught at commit time never enter the repo. Caught in CI, they are already in your git history.

## Attribution

Based on techniques from the Coding Agents: AI Driven Dev Conference. Sid (Anthropic) on preferring pre-commit hooks over per-edit hooks for less disruptive flow. Josh on using lifecycle hooks to enforce linting, tests, and compilation, and on creating immutable tests the agent cannot modify. Yari on LLM-powered auto-approval hooks for permission prompts. Milan (Semgrep) on audit trail hooks for logging every shell command with timestamps and scanning agent-generated code with security tools before shipping.
