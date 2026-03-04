---
name: agent-maintained-docs
description: Use when creating new files, modifying existing files, adding new folders, or making structural changes to a codebase and you want documentation that agents (and humans) can grep/search to navigate the project.
---

# Agent-Maintained Documentation

## Overview

A technique for keeping codebase documentation perpetually current by embedding it directly in source files and enforcing updates through commit-time hooks. Every file gets a header comment describing its purpose, every folder gets a README, and a validation hook rejects commits where code changed but docs did not.

**Core principle:** Documentation is a codebase navigation tool for agents. When an agent greps for "authentication" or "payment processing," file header comments and folder READMEs surface the right files instantly. Agents will reliably maintain these docs if you enforce it -- humans will not.

**Dependency:** A git hooks mechanism (husky, lefthook, pre-commit, or a bare `.git/hooks/pre-commit` script).

## When to Use

- When creating any new file in the project
- When modifying a file's purpose, exports, or public interface
- When adding a new folder or reorganizing the project structure
- When onboarding agents to an existing codebase that lacks navigability
- When multiple agents (or agent sessions) work across the same repo

## When NOT to Use

- Trivial internal implementation changes that do not alter a file's purpose or interface
- Auto-generated files (build output, lockfiles, compiled assets)
- Third-party vendored code you do not own

## Common Mistakes

| Mistake | Why it's wrong |
|---------|---------------|
| Writing docs only in a top-level wiki or docs site | Agents navigate by grepping the source tree. Docs outside the source tree are invisible to file-level search. |
| Trusting humans to keep file headers updated | They won't. Rob: "Agents maintain docs reliably if enforced; humans don't." Enforce with hooks or it decays within weeks. |
| Putting implementation details in the header comment | Header comments describe *what* and *why*, not *how*. Implementation details change constantly and create noisy diffs. |
| Skipping the commit-time validation hook | Without enforcement, the practice erodes immediately. The hook is what makes this sustainable. |
| Writing vague one-word descriptions like "Utils" or "Helpers" | These are useless for search. A header should tell an agent exactly what functionality lives in this file so grep returns meaningful hits. |

## Step 1: Add header comments to every file

Every source file gets a block comment at the very top (before imports) describing what the file does, what it exports, and why it exists. Use the comment syntax native to the file's language.

**TypeScript / JavaScript:**

```typescript
/**
 * @file Authentication middleware for Express routes.
 * @purpose Validates JWT tokens, attaches user context to req.user,
 *          and rejects unauthenticated requests with 401.
 * @exports authMiddleware - Express middleware function
 * @exports requireRole(role) - Factory that returns middleware restricting by role
 */

import { Request, Response, NextFunction } from 'express';
// ... rest of file
```

**Python:**

```python
"""
File: payment_processor.py
Purpose: Handles Stripe payment intents, refunds, and webhook verification.
Exports:
    create_payment_intent(amount, currency) - Creates a Stripe PaymentIntent
    process_refund(payment_id, reason) - Issues a full or partial refund
    verify_webhook(payload, signature) - Validates incoming Stripe webhooks
"""

import stripe
# ... rest of file
```

**Go:**

```go
// File: internal/cache/redis.go
// Purpose: Redis-backed cache layer with TTL support and connection pooling.
// Exports:
//   NewRedisCache(addr, password, db) - Constructor
//   Cache.Get(key) - Retrieve cached value
//   Cache.Set(key, value, ttl) - Store with expiration
//   Cache.Invalidate(pattern) - Delete keys matching glob pattern

package cache
```

**Key rules for header comments:**

- Describe *what* the file does, not *how* it does it internally
- List public exports/functions so grep finds them
- Include enough domain terms that an agent searching for a concept will hit this file
- Keep it under 10 lines -- this is a signpost, not a manual

## Step 2: Add a README.md to every folder

Each folder gets a short README explaining what lives in that folder, why it is separated from other folders, and listing its contents with one-line descriptions.

**Template:**

```markdown
# /src/services/

## Purpose

Business logic services that orchestrate between controllers and data access.
Each service owns one domain concept and exposes a clean async interface.

## Contents

| File | Description |
|------|-------------|
| `auth.service.ts` | User authentication, token generation, and session management |
| `billing.service.ts` | Subscription lifecycle, invoice generation, Stripe integration |
| `notification.service.ts` | Email, SMS, and push notification dispatch |
| `user.service.ts` | User CRUD, profile updates, and account deactivation |

## Conventions

- Services never import from controllers (dependency flows inward)
- All public methods return Promises
- Errors throw typed exceptions from `/src/errors/`
```

**Key rules for folder READMEs:**

- The table of contents must list every file in the folder
- When a file is added or removed, the README must be updated in the same commit
- Keep descriptions to one line -- enough for an agent to decide whether to read the file
- Include any folder-specific conventions or patterns

## Step 3: Configure commit-time validation

Install a pre-commit hook that checks whether documentation was updated alongside code changes. This is the enforcement mechanism that makes the practice sustainable.

**Using a bare git hook (`.git/hooks/pre-commit`):**

```bash
#!/usr/bin/env bash
set -euo pipefail

# Get list of staged files (Added, Modified, Renamed)
STAGED_FILES=$(git diff --cached --name-only --diff-filter=AMR)

MISSING_DOCS=()

for file in $STAGED_FILES; do
  # Skip non-source files
  case "$file" in
    *.md|*.json|*.lock|*.yaml|*.yml|*.toml|*.gitignore) continue ;;
  esac

  # Check 1: New files must have a header comment in the first 10 lines
  if git diff --cached --diff-filter=A --name-only | grep -q "^${file}$"; then
    HEAD_LINES=$(git show ":${file}" | head -10)
    if ! echo "$HEAD_LINES" | grep -qiE '(@file|@purpose|^#.*Purpose:|^"""$|^/\*\*$)'; then
      MISSING_DOCS+=("NEW file missing header comment: $file")
    fi
  fi

  # Check 2: If a source file changed, its folder README must also be staged
  DIR=$(dirname "$file")
  README="${DIR}/README.md"
  if [ -f "$README" ] && ! echo "$STAGED_FILES" | grep -q "^${README}$"; then
    # Only warn if a file was added or deleted in that folder
    FOLDER_ADDS=$(git diff --cached --diff-filter=AD --name-only | grep "^${DIR}/" || true)
    if [ -n "$FOLDER_ADDS" ]; then
      MISSING_DOCS+=("Folder README not updated: $README (files added/removed in $DIR)")
    fi
  fi
done

if [ ${#MISSING_DOCS[@]} -gt 0 ]; then
  echo "========================================="
  echo " Documentation validation failed"
  echo "========================================="
  for msg in "${MISSING_DOCS[@]}"; do
    echo "  - $msg"
  done
  echo ""
  echo "Fix: Add header comments to new files and update folder READMEs."
  echo "Skip (emergency only): git commit --no-verify"
  exit 1
fi
```

**Using Husky + lint-staged (Node projects):**

```json
// package.json
{
  "lint-staged": {
    "*.{ts,tsx,js,jsx}": [
      "node scripts/check-file-header.js"
    ]
  }
}
```

```javascript
// scripts/check-file-header.js
const fs = require('fs');

const files = process.argv.slice(2);
const failures = [];

for (const file of files) {
  const head = fs.readFileSync(file, 'utf-8').split('\n').slice(0, 10).join('\n');
  if (!/@file|@purpose/i.test(head)) {
    failures.push(file);
  }
}

if (failures.length > 0) {
  console.error('Files missing @file/@purpose header comment:');
  failures.forEach(f => console.error(`  - ${f}`));
  process.exit(1);
}
```

## Step 4: Bootstrap an existing codebase

When applying this to a project that lacks documentation, run a one-time bootstrapping pass:

1. **List all source files** without header comments
2. **Read each file** and generate a header comment from its contents
3. **List all folders** without READMEs
4. **Generate a README** for each folder from its file listing
5. **Commit the bootstrap** as a single commit: `docs: bootstrap file headers and folder READMEs`
6. **Install the hook** so all future changes are enforced

This bootstrapping is an ideal task for an agent. It can read every file, summarize its purpose, and write the headers far faster and more consistently than a human.

## Quick Reference

| Item | Location / Convention |
|------|----------------------|
| File header comment | First 5-10 lines of every source file, before imports |
| Folder README | `README.md` in every folder containing source files |
| Pre-commit hook | `.git/hooks/pre-commit` or via husky/lefthook/pre-commit |
| Header format (JS/TS) | `/** @file ... @purpose ... @exports ... */` |
| Header format (Python) | Triple-quote docstring with File/Purpose/Exports |
| Header format (Go) | `// File: ... // Purpose: ... // Exports: ...` |
| Hook skip (emergency) | `git commit --no-verify` |

## Key Principles

1. **Documentation is a navigation tool, not a formality.** The sole purpose of file headers and folder READMEs is to make grep and search effective for agents navigating the codebase.
2. **Enforce with hooks, not discipline.** Agents will maintain docs reliably when a hook rejects commits that skip updates. Without enforcement, the practice decays immediately.
3. **Agents maintain docs; humans don't.** This is an empirical observation. Agents follow instructions consistently. Lean into that strength by making doc-maintenance an agent responsibility.
4. **Headers describe *what* and *why*, never *how*.** Implementation details change constantly. A header that says "Validates JWT tokens and attaches user context" survives refactors. One that says "Uses jsonwebtoken v9 with RS256" breaks on the next dependency update.
5. **Every file, every folder, every commit.** Partial adoption provides partial value. The compounding benefit comes from knowing that *any* grep hit will have context attached.

## Attribution

Based on Rob's technique from the Coding Agents: AI Driven Dev Conference [03:42:50 - 03:43:30]. Rob advocates adding documentation comments to the top of every file and a README per folder, validating at commit time that docs stay current, and observes that agents maintain documentation reliably when enforced -- humans do not.
