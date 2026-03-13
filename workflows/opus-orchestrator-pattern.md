# Justin's Opus Orchestrator Pattern

## When to Use This

You have multiple features to build in parallel and want ONE agent managing everything without you juggling multiple agent contexts. Use this for projects with:
- 3+ independent features that can progress simultaneously
- Complex coordination needs between parallel streams
- A desire to get multiple PRs from a single orchestration session

## Prerequisites

- Claude Opus 4.6 available (ideally not constrained by token limits)
- Git repository with branch support
- Agent framework that can spawn sub-agents or parallel processes
- Superpowers Git plugin (optional but recommended for automatic sub-agent suggestions)

## The Orchestrator Pattern

### Phase 1: Research & Planning

1. Gather all requirements, specs, and architecture documentation
2. Identify dependencies between tasks
3. Determine what can run in parallel vs what must be sequential
4. Create a map showing:
   - Task A → Task B → Task C (sequential)
   - Task D and Task E (parallel to each other and to A-B-C)

**Example breakdown:**
```
Feature: Multi-language support + Dark mode + Performance metrics

Sequential bottleneck: Update database schema (affects all three)

Then parallel:
- Feature A: I18n (translation system, no UI dependencies)
- Feature B: Dark mode (CSS/theme system)
- Feature C: Metrics dashboard (reporting endpoints)

All three can run simultaneously after schema migration.
```

### Phase 2: The One-Liner Briefing

Give Opus ONE instruction (in a single message):

```
Here's the project state: [context]

Work breakdown:
1. (Sequential) Update schema with lang_code and theme_preference columns
2. (Parallel) Build i18n system, dark mode theme, metrics collection

You will spin up three sub-agents to handle features A, B, and C simultaneously.
Report back with your plan for how you'll coordinate them, then execute.
I only want to interact with you. You manage everything internally.
```

**Key points:**
- Explicitly state which tasks are parallel
- Tell the agent you'll only interact with the orchestrator, not sub-agents
- Ask for a plan report before execution

### Phase 3: Orchestrator Manages Everything

The Opus agent:
1. Plans how to set up sub-agents
2. Identifies which work trees or branches each needs
3. Spins up sub-agents in "background" (in internal context)
4. Coordinates them:
   - Ensures sequential tasks complete before parallel ones start
   - Handles merge conflicts if they arise
   - Communicates requirements between agents
5. Consolidates results
6. Creates multiple PRs (one per feature)

**You don't:**
- Switch between agent windows
- Check individual agent status
- Manage merge conflicts manually
- Coordinate between parallel work streams

**The orchestrator handles all of it.**

### Phase 4: Multi-PR Review

The orchestrator delivers:
- 5 different PRs (one per major component)
- Each with clear commit history
- All reviewable independently
- All mergeable (conflicts already resolved)

## Using Work Trees Efficiently

Orchestrator creates a work tree per parallel feature:

```
Main branch (shared schema work)
├── work-tree-i18n/ (Feature A)
├── work-tree-dark-mode/ (Feature B)
└── work-tree-metrics/ (Feature C)
```

**Why work trees over full clones:**
- Much faster to set up
- Lower disk footprint
- Shared git objects
- Orchestrator still isolates work per feature

## Superpowers Git Plugin Integration

If available, the plugin helps by:
1. Suggesting how to split work into sub-agents automatically
2. Proposing branch strategy per feature
3. Identifying merge conflict risks upfront
4. Recommending commit granularity for reviewability

You can ignore its suggestions, but it saves planning time.

## Workflow Example

```
Your instruction:
"I have 3 features: auth refactor, mobile UI, payment processing.
Auth refactor is blocking the other two. After that, mobile and payment
run in parallel. Plan it, spin up sub-agents, execute, give me 3 PRs."

Opus response:
"Plan: I'll create sequential work for auth, then fork into two parallel
work trees. Using git work trees to isolate. Sub-agent-auth will handle
schema + logic. Sub-agent-mobile will build on new auth. Sub-agent-payment
will integrate with new auth. Timeline: auth ~30 min, then parallel 45 min.
Executing now. You'll see 3 PRs on GitHub in ~1.5 hours."

[Orchestrator manages everything internally]

30 minutes later:
"Auth refactor merged. Mobile and payment sub-agents now running in parallel."

45 minutes later:
"Three PRs created:
- PR #142: Auth refactor (9 commits)
- PR #143: Mobile UI responsive (12 commits)
- PR #144: Payment processing (8 commits)
All tests passing. Ready for review."
```

## Tips & Gotchas

**Tip:** Be explicit about parallel vs sequential in your briefing. Vague sequencing leads to sub-agents waiting or stepping on each other.

**Gotcha:** The orchestrator is smart but has limits. If there are circular dependencies between parallel tasks, it will get stuck. Map your dependencies carefully upfront.

**Tip:** Large projects benefit most from this pattern. For 2-3 small features, the overhead isn't worth it.

**Gotcha:** Token context limits can become an issue if parallel work is heavy. Opus 4.6's context window helps, but massive features might need manual splitting.

**Tip:** Ask the orchestrator for periodic status updates. It won't volunteer unless you request it.

**Gotcha:** Don't expect perfect commit history. The orchestrator optimizes for correctness, not aesthetics. You may want to squash-merge or rebase before production if git history matters.

**Tip:** Use this pattern with a code review gate. Multiple PRs from parallel work streams increase merge risk.

## When NOT to Use This Pattern

- Single feature development (use Plan-Build-Punch instead)
- Highly interdependent work (too much coordination overhead)
- Real-time collaboration needed (async orchestration doesn't handle that well)
- Team of humans building simultaneously (use this for agents, not humans)
