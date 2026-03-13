---
name: merge-conflict-resolution
description: Use when merging parallel agent work or branches to resolve both syntactic merge conflicts (merge markers) and semantic conflicts (contradictory logic, API changes, schema mismatches) that traditional merge tools miss.
---

# Merge Conflict Resolution

## Overview

The Merge Conflict Resolution Skill resolves both syntactic AND semantic merge conflicts from parallel agent work. This skill is essential when multiple agents or developers work on overlapping code simultaneously. While traditional merge tools catch syntax conflicts (merge markers), they miss semantic conflicts—situations where two changes logically contradict each other even though they don't overlap syntactically.

**Core principle:** Semantic conflicts are invisible to git but deadly at runtime. A human-like understanding of intent is required to resolve them correctly.

**Dependency:** Claude Code CLI with git and test infrastructure.

## When to Use

- Merging multiple branches that touched overlapping code
- Combining work from parallel agents working on the same system
- After complex refactors that affect shared abstractions
- When API or schema changes intersect with dependent code
- Before considering a merge complete and ready to deploy

## When NOT to Use

- Simple, fast-forward merges with no conflicts
- Merging unrelated branches (separate features, independent systems)
- Trivial merge conflicts (auto-mergeable, single-line disagreements)

## Common Mistakes

| Mistake | Why it's wrong |
|---------|---------------|
| Only resolving merge markers | Merge markers are the easy part. Semantic conflicts—logical contradictions—are what break code at runtime. |
| Not reading all commits/PRs since divergence | You need the full story of what both sides were trying to do. One commit in isolation won't tell you that. |
| Choosing one design without understanding both | Before picking A or B, understand the intent behind each. Sometimes a hybrid approach preserves both improvements. |
| Trusting test results if they pass silently | If the coding agent made assumptions, those same assumptions are baked into validation. Use fresh context to catch real issues. |
| Not flagging design decisions | If you chose one approach over another because it seemed better, but it's not objectively right, flag it for human review. |

## The Resolution Process

### Step 1: Gather Context

First, understand what we're working with:
- Current branch: (confirm)
- Branch being merged: (confirm)
- Time period: When was the divergence?
- Number of PRs/commits involved: How much work are we merging?

Ask the user to provide:
- The branch name or commit SHAs
- Any context about what work was happening in parallel
- Which system(s) or files are most critical to get right

### Step 2: Read All Recent Commits

Fetch and summarize every commit/PR since the divergence.

For each commit, extract:
- **What changed**: Files modified, lines changed
- **Why**: Commit message and intent
- **Type**: Feature, refactor, bugfix, or schema change
- **Scope**: What subsystems are affected

Create a table:
| Commit | Intent | Type | Files Modified | Critical? |
|--------|--------|------|----------------|-----------|
| [SHA/PR] | [summary] | [type] | [list] | [yes/no] |

### Step 3: Identify Syntactic Conflicts

Run:
```bash
git diff --name-only --diff-filter=U
```

For each file with merge markers:
- Show the conflict block
- Explain what each side is trying to do
- Propose resolution

Mark each as: "Keep A", "Keep B", "Keep both (reorder)", "Combine with modifications", "Choose A with B's intent"

### Step 4: Identify Semantic Conflicts

This is the critical step. For each commit, ask:
- Does this assume something about code that another commit changed?
- Do two commits make contradictory design decisions?
- Is there a dependency between commits that create a logical contradiction?

Common patterns to check:
- **API changes**: Are both sides extending the same API in incompatible ways?
- **Database schema**: Did one side add/drop/rename columns that the other side assumes exist?
- **Configuration**: Did both sides change the same config key to different values?
- **Abstractions**: Did one side refactor a shared function that the other side relies on?
- **Imports and paths**: Did one side move/rename modules that the other side imports from?

For each semantic conflict found, document:
- **Conflict**: What's the contradiction?
- **Source**: Which commits created this?
- **Impact**: What will break if we don't resolve this?
- **Resolution options**: A, B, or combine?

Example semantic conflict:
```
Conflict: Agent A redesigned UserService API (removed `getUserById`, added `getUser`)
          Agent B added code calling the old `getUserById` method
Impact: Runtime error - method does not exist
Options:
  A) Update Agent B's code to use new `getUser` method
  B) Keep both methods (one calls the other)
  C) Revert Agent A's refactor (probably not, it's an improvement)
```

### Step 5: Resolve All Conflicts

For each syntactic conflict:
- Edit the file to resolve merge markers
- Test that syntax is valid (if possible)

For each semantic conflict:
- Choose the resolution strategy
- Make the necessary changes across files
- Ensure consistency

Preserve intent: If Agent A was improving code quality and Agent B was adding features, don't lose the improvement.

### Step 6: Validate Resolutions

After resolving all conflicts:

**Code validation**:
- Check syntax: `eslint`, `pylint`, or equivalent
- Check imports: All imports valid?
- Check function signatures: Are all calls compatible with definitions?
- Grep for "TODO" or markers you added

**Logic validation**:
- Review any modified business logic
- Ensure error handling is consistent
- Check database migrations are in correct order

**Test validation** (if tests exist):
- Run test suite on merged branch
- Flag any failing tests

### Step 7: Compile Resolution Report

Provide a structured summary:

```
## Merge Conflict Resolution Report

**Merging**: [branch name] into [target branch]

### Syntactic Conflicts Resolved
- [file]: [resolution summary]
- [file]: [resolution summary]

### Semantic Conflicts Resolved
1. **API Redesign Conflict**
   - Problem: Agent A redesigned UserService, Agent B uses old API
   - Resolution: Updated Agent B's code to use new methods
   - Files affected: [list]

2. **Schema Mismatch Conflict**
   - Problem: Agent A removed a column, Agent B selects it
   - Resolution: Updated query in Agent B's code
   - Files affected: [list]

### Validation Status
- [ ] Syntax check passed
- [ ] All imports valid
- [ ] Function signatures consistent
- [ ] Tests passing (or note which tests fail)
- [ ] Manual review completed

### Flags for Human Review
- [If any] Testing failures that need investigation
- [If any] Unresolvable conflicts that require human decision
- [If any] Places where I chose one design over another—confirm this was right

### Ready to Commit
YES / NO (explain if no)
```

### If Fully Blocked

If you encounter a semantic conflict you can't resolve without human input:
- Explain the conflict clearly
- Present both options with tradeoffs
- Flag it for human decision
- Note what you can do once decision is made

## Key Principles

1. **Preserve intent**: Don't lose improvements made by either agent
2. **Maintain consistency**: One design decision should apply everywhere
3. **Minimize changes**: Only change what's necessary to resolve conflicts
4. **Test and validate**: Make sure the merge actually works
5. **Flag uncertainty**: Don't silently make design decisions; ask for confirmation

## Configuration Notes

### Project-Specific Setup

1. **Test command**: Update the validation step with your project's test command:
   ```
   Test command: `npm test` / `pytest` / `cargo test` / etc.
   ```

2. **Linting rules**: Specify your project's linting:
   ```
   Linting: `eslint .` / `pylint src/` / etc.
   ```

3. **Schema validation**: If you use database migrations:
   ```
   Check: Are migrations in chronological order?
   Check: Do migrations match code assumptions?
   ```

4. **API documentation**: Reference where API contracts are documented:
   ```
   API definitions: `/api/openapi.yaml` or equivalent
   Schema definitions: `/schema/` or equivalent
   ```

## How to Invoke

From your main coding session, create a sub-agent or context and invoke:

```
/merge-conflict-resolution

Branch to merge: [branch name]
Target branch: [target branch]
```

Or after hitting merge conflicts:

```
I have merge conflicts between [branch A] and [branch B].
Use the merge conflict resolution skill to resolve them.
```

## Tips from Practitioners

**When to run this**: Immediately after merging, before considering the merge "done."

**Communication with merged agents**: If Agent A and Agent B worked in parallel, brief them on the semantic conflicts resolved. They may have context about why they made certain decisions.

**Design decisions**: When you encounter a true design conflict (two valid approaches), consider:
- Which was implemented first in the original codebase?
- Which is more aligned with the project's architecture?
- Which is easier to maintain long-term?

**Prevention**: To reduce merge conflicts:
- Document critical APIs and schema changes
- Run this skill *before* merging, when possible
- Use architectural patterns that reduce coupling between parallel work

**Pro tip**: Save detailed merge reports. When a semantic conflict causes issues later, you'll have documentation of the decision made.

## Attribution

Based on techniques from the Coding Agents Lunch & Learn Series. Rob Ennals (Anthropic) contributed the core insight: "Agents are really good at resolving merge conflicts... This is the kind of grunt work which agents are really good at. The human doesn't have to orchestrate careful coordination between agents before they start."
