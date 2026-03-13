# Rob's Parallel Agent Workflow with Broomy

## When to Use This

You're running 5+ agents in parallel and need unified visibility into what they're doing. Use Broomy when:
- Manual agent window switching is becoming painful
- You can't remember which agent is stuck or idle
- You want custom commands that trigger different skills per agent
- You want to stay productive while agents work (not context-switching constantly)

## Prerequisites

- Broomy installed and running
- Claude Code, Cursor, or Gemini editor available
- Multiple agent instances (5+) worth managing
- Git work trees set up per agent (recommended)
- Agent skills/prompts defined for common tasks

## What Is Broomy?

Broomy is an Electron-based UI that sits ON TOP of your editor (VS Code, Cursor, Gemini). It doesn't replace them—it augments them.

**Layout:**
- **Right side:** Your normal editor (VS Code/Cursor/Gemini)
- **Left side:** Panel showing all parallel agent sessions with status
- **Bottom:** Customizable command buttons

## Architecture & Setup

### Session Dashboard

Left panel displays all agents:

```
Agent Status Dashboard
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
🟢 agent-auth     [WORKING] ████████░░ 60%
🟡 agent-mobile   [READY]   Task queued
🟢 agent-backend  [WORKING] ████░░░░░░ 30%
⚪ agent-docs     [IDLE]    Waiting for input
🟢 agent-tests    [WORKING] ████████░░ 75%
```

**Status indicators:**
- 🟢 WORKING: Currently executing
- 🟡 READY: Task accepted, waiting to start
- ⚪ IDLE: Not assigned work
- 🔴 STUCK: No progress reported in timeout period

Progress bars show estimated completion.

### Customizable Command Buttons

Define buttons once, they trigger different skills per agent:

**Button: "Commit This Work"**
- agent-auth: runs commit-prompt skill, creates semantic commit
- agent-mobile: same skill, commits current branch
- agent-backend: same skill, commits
- Result: 5 parallel commits, all semantic

**Button: "Write All Tests"**
- Sends "write comprehensive unit tests" to all IDLE agents
- WORKING agents ignore it
- Result: test coverage increases in parallel

**Button: "Merge All Conflicts"**
- Each agent auto-resolves conflicts in its own work tree
- Broomy collects all resolutions, flags any that need human review

**Button: "You Appear Stuck"**
- Sends diagnostics query to agents not reporting progress
- Agent responds with: what it's doing, why it's stuck, what it needs
- You can unblock directly instead of guessing

**Button: "Review Major Decisions"**
- Agents summarize architectural choices made in their branches
- Broomy aggregates into a single review doc
- You catch design conflicts before merge

**Custom buttons you might add:**
- "Push to staging"
- "Run security scan"
- "Generate changelog"
- "Explain what you changed"

## Parallel Workflow

### Phase 1: Setup (One Time)

1. Define your 5-6 parallel features/tasks
2. Create a work tree per agent
3. Spin up agent instances (one per work tree)
4. Configure Broomy:
   - Add agent names to dashboard
   - Define your command buttons
   - Set status update frequency
5. Test one button to confirm it works

### Phase 2: Assign Work

1. Open Broomy dashboard
2. Click agent → queue task/send prompt
3. Each agent gets the same high-level instruction, adapted for their feature:

```
"Build the X component for the mobile app.
Architecture: Use Redux for state, Material-UI for components.
Acceptance: Component renders, integrates with API, tests pass.
You have 30 minutes."
```

All agents start working. You stay in Broomy.

### Phase 3: Monitor & Manage

**Stay in work mode, not phone-scroll mode.**

Instead of switching windows constantly:
- Glance at Broomy left panel (always visible)
- See which agents are working, which are ready for input
- Use command buttons for bulk operations
- Only click into an agent's window if it's specifically stuck

**When an agent reports STUCK:**
- Click on it → see recent context
- Ask: "What's blocking you?"
- Get precise answer (not guessing)
- Unblock and continue

### Phase 4: Converge

When agents finish:

1. **Merge conflicts:** All resolved by Broomy
2. **Tests:** All passing (agents wrote them)
3. **Code review:** All within current window
4. **Commit history:** Semantic and reviewable
5. **Multiple PRs:** Ready to push

Result: 5 independent, merge-ready PRs with full git history.

## Command Button Examples

### "Commit This Work"

```yaml
button_name: "Commit This Work"
agents:
  - all

command: |
  You are ready to commit your work.
  Use clear, semantic commit messages.
  Format: "type(scope): description"
  Example: "feat(auth): add password reset flow"
  Commit now.
```

### "Merge All Conflicts"

```yaml
button_name: "Merge All Conflicts"
agents:
  - all

command: |
  You have conflicts in your work tree.
  Resolve them based on these principles:
  1. Prefer changes from main branch if ambiguous
  2. Keep business logic from your feature
  3. Test after each conflict resolution
  Merge when clean.
```

### "Generate Architecture Summary"

```yaml
button_name: "Explain Everything"
agents:
  - all

command: |
  Summarize what you built:
  1. High-level feature description
  2. Key files modified
  3. Database schema changes (if any)
  4. API contracts added/changed
  5. Test coverage (%)
  Keep it to 5 minutes of reading.
```

## Philosophy: Developer-First Design

**Rob's principle:** "Start with developers where they are."

Broomy doesn't force a new workflow. It:
- Augments existing editors (right side still works normally)
- Adds visibility (left dashboard)
- Provides shortcuts (buttons)
- Removes context-switching pain

You still edit code in VS Code. You just have supervision of all agents without micromanaging.

## Tips & Gotchas

**Tip:** Set status update frequency to 30 seconds. More frequent = CPU overhead. Less frequent = stale info.

**Gotcha:** If you define a button wrong, ALL agents execute it wrong. Test button behavior on one agent first.

**Tip:** Use work trees, not full clones. Sets up 10+ agents in seconds instead of minutes.

**Gotcha:** Agents might not know how to use Broomy buttons. Frame instructions explicitly: "When you see 'Commit This Work' queued, here's what to do..."

**Tip:** Stuck indicators are heuristic-based (no progress for N seconds). False positives happen. Ask the agent before assuming it's truly stuck.

**Gotcha:** Don't spin up more agents than your CPU can handle. 5-6 concurrent agents is usually the sweet spot.

**Tip:** Broomy works with Cursor, Claude Code, and Gemini. Use the one your team prefers.

**Gotcha:** If agents produce conflicting changes (both touch the same files), Broomy flags conflicts but you still resolve them. Have a conflict resolution strategy ready.

## Sample Session

```
[You open Broomy dashboard]

Agents initialized:
- agent-api (auth feature)
- agent-frontend (mobile UI)
- agent-db (schema migration)
- agent-tests (coverage)
- agent-docs (API docs)

[You click agent-api, type prompt]
"Build user authentication with JWT refresh tokens.
Must integrate with new database schema.
Tests and API docs required."

[Broomy queues this to agent-api]
[You send similar instructions to other agents]

🟢 agent-api:     [WORKING] ████████░░ 60%
🟡 agent-frontend: [READY]   Task queued
🟢 agent-db:      [WORKING] ████░░░░░░ 25%
⚪ agent-tests:   [IDLE]    Waiting for input
🟢 agent-docs:    [WORKING] ████░░░░░░ 40%

[You don't switch windows. You're in Broomy.]
[30 minutes pass. You glance at dashboard occasionally.]

🟢 agent-api:     [WORKING] ██████████ 100%
🟢 agent-frontend: [WORKING] ████████░░ 75%
🟡 agent-db:      [READY]   Merge conflict detected
⚪ agent-tests:   [IDLE]    Awaiting coverage goals
🟢 agent-docs:    [WORKING] ███████░░░ 85%

[You click "Merge All Conflicts" button]
[Broomy sends conflict resolution command to all agents]

[20 seconds later]
🟡 agent-db:      [READY]   Conflict resolved, awaiting approval

[You click conflict → see resolution → approve]

[Continue monitoring]
[1.5 hours later, all agents report READY]

[Click "Generate Architecture Summary"]
[5 summaries appear in Broomy]
[You review, ask clarifying questions, then]

[Click "Commit This Work"]
[All agents commit in parallel]

[All 5 agents READY for push]
[Result: 5 PRs on GitHub, all clean, all reviewable]
```

## When NOT to Use Broomy

- Single developer, single agent (overhead isn't worth it)
- Highly synchronous work (agents need constant feedback)
- Text-only, no UI component (no progress visibility benefit)
