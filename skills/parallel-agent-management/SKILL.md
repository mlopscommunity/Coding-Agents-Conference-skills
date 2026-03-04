---
name: parallel-agent-management
description: Use when you need to run multiple Claude Code agents simultaneously on different parts of a codebase, or when a task is large enough to benefit from decomposition into parallel sub-tasks with clear contracts.
---

# Parallel Agent Management

## Overview

A structured approach to running multiple Claude Code agents in parallel using git worktrees, containers, and explicit communication contracts. The key insight is that the bottleneck with parallel agents is organization, not capability. Invest in the scaffolding before spinning up agents.

**Core principle:** One main agent orchestrates, one layer of sub-agents executes. Keep the hierarchy flat. Every sub-agent gets an explicit contract specifying exactly what to do and exactly what to return.

**Dependencies:** Git (for worktrees), optionally Docker (for container isolation).

## When to Use

- Large refactors that touch independent modules simultaneously
- Feature work where frontend, backend, and tests can proceed in parallel
- Exploratory work where you want multiple approaches tried at once
- Any task where you find yourself thinking "I wish I could work on this other part while waiting"

## When NOT to Use

- Small, sequential changes where one agent finishes in minutes
- Tightly coupled code where every change depends on the previous one
- When you don't have time to set up the scaffolding (the setup IS the investment)
- Tasks requiring deep, single-threaded reasoning across the whole codebase

## Common Mistakes

| Mistake | Why it's wrong |
|---------|---------------|
| Deep agent hierarchies (agents spawning agents spawning agents) | Niels: One main agent + one layer of sub-agents is sufficient for most cases. Deeper nesting creates coordination nightmares and lost context. |
| Vague sub-agent instructions ("fix the tests") | Harrison Chase: Sub-agents need explicit communication contracts. Specify the exact task, input format, expected output format, and success criteria. |
| Running parallel agents in the same worktree | Agents will clobber each other's file changes. Each agent needs its own isolated worktree or container. |
| Skipping the orchestration step | Jumping straight to "run 5 agents" without planning which tasks are independent, what the interfaces are, and how results merge back. The organization IS the work. |
| Using `--dangerously-skip-permissions` on bare metal | Rob: Run agents in containers to safely use `--dangerously-skip-permissions`. On bare metal, a runaway agent can damage your system. |
| Not having a switching mechanism between worktrees | Without quick switching (Alfred, keybinds, tmux), you lose time context-switching. Sid uses Alfred/AppleScript automation to jump between five predefined worktrees. |

## Step 1: Set Up Worktrees

Create dedicated worktrees for parallel work. Five is a practical upper bound for active management.

```bash
# Create worktrees from your repo root
git worktree add ../project-agent-1 -b agent/feature-api
git worktree add ../project-agent-2 -b agent/feature-ui
git worktree add ../project-agent-3 -b agent/feature-tests
git worktree add ../project-agent-4 -b agent/refactor-models
git worktree add ../project-agent-5 -b agent/spike-perf

# List active worktrees
git worktree list
```

Each worktree is a full working copy on its own branch. Agents in separate worktrees cannot conflict on file writes.

### Quick-Switch Setup (Optional but Recommended)

For macOS with Alfred or Raycast, create shortcuts that open terminals in each worktree:

```bash
# Example: shell aliases for fast switching
alias wa1="cd /path/to/project-agent-1 && echo 'Agent 1: feature-api'"
alias wa2="cd /path/to/project-agent-2 && echo 'Agent 2: feature-ui'"
alias wa3="cd /path/to/project-agent-3 && echo 'Agent 3: feature-tests'"
```

For tmux users, create named sessions per worktree:

```bash
tmux new-session -d -s agent1 -c /path/to/project-agent-1
tmux new-session -d -s agent2 -c /path/to/project-agent-2
tmux new-session -d -s agent3 -c /path/to/project-agent-3
```

## Step 2: Container Isolation (For Autonomous Agents)

When you want agents to run autonomously with `--dangerously-skip-permissions`, use containers so a runaway agent cannot damage your host system.

```dockerfile
# Dockerfile.claude-agent
FROM node:20-slim
RUN npm install -g @anthropic-ai/claude-code
WORKDIR /workspace
# Mount the worktree as a volume at runtime
```

```bash
# Run an agent in a container with the worktree mounted
docker run --rm -it \
  -v /path/to/project-agent-1:/workspace \
  -e ANTHROPIC_API_KEY="$ANTHROPIC_API_KEY" \
  claude-agent \
  claude --dangerously-skip-permissions \
    -p "Implement the REST API endpoints for user management. Return a summary of files created and any open questions."
```

Use a tool like Broomy or a custom script to manage multiple containerized agents simultaneously -- starting, monitoring, and collecting their outputs.

## Step 3: Define Sub-Agent Contracts

Every sub-agent must receive an explicit communication contract. Vague instructions produce vague results that are expensive to reconcile.

### Sub-Agent Prompt Template

```
## Task
[One sentence describing exactly what to build or change]

## Context
- Branch: [branch name]
- Working directory: [path]
- Related files: [list the specific files this agent should read/modify]
- Dependencies: [what this task depends on, if anything]

## Input
[Describe any input data, schemas, or interfaces the agent should use]

## Expected Output
- [ ] [Specific file or change 1]
- [ ] [Specific file or change 2]
- [ ] [Specific file or change 3]

## Return Format
When complete, provide:
1. A list of all files created or modified
2. Any deviations from the plan and why
3. Open questions or decisions that need human input
4. A one-line summary of what was done

## Constraints
- Do NOT modify files outside [specific directory]
- Do NOT change the public API signatures in [file]
- All new code must include tests
- If you hit a blocker, document it and move on to the next item
```

## Step 4: Orchestrate and Monitor

The main agent (you, or a coordinating agent) is responsible for:

1. **Decomposing** the work into independent tasks
2. **Assigning** each task to a worktree with a contract
3. **Monitoring** progress (check outputs, review git logs)
4. **Merging** results back into the main branch

```bash
# Monitor agent progress across worktrees
for dir in ../project-agent-{1,2,3,4,5}; do
  echo "=== $(basename $dir) ==="
  git -C "$dir" log --oneline -3
  echo ""
done
```

### Merging Results

```bash
# From the main repo, merge each agent's branch
git merge agent/feature-api --no-ff -m "Merge agent: REST API endpoints"
git merge agent/feature-ui --no-ff -m "Merge agent: UI components"
git merge agent/feature-tests --no-ff -m "Merge agent: test coverage"

# Clean up worktrees when done
git worktree remove ../project-agent-1
git worktree remove ../project-agent-2
git worktree remove ../project-agent-3
```

## Step 5: Keep Idea Sessions Running

Maintain 5-10 Claude Code web sessions throughout the day for capturing and exploring random ideas. These are separate from your focused parallel worktree agents. When an idea matures, promote it to a worktree with a proper contract.

## Quick Reference

| Item | Details |
|------|---------|
| Max recommended worktrees | 5 active (more becomes hard to track) |
| Agent hierarchy depth | 2 levels max (orchestrator + sub-agents) |
| Sub-agent contract | Must specify: task, input, expected output, return format, constraints |
| Container flag | `--dangerously-skip-permissions` (containers only) |
| Worktree creation | `git worktree add <path> -b <branch>` |
| Worktree cleanup | `git worktree remove <path>` |
| Idea sessions | 5-10 Claude Code web sessions for exploration |
| Monitoring | Check `git log` in each worktree, review agent outputs |

## Key Principles

1. **The bottleneck is organization, not capability.** Invest in scaffolding (worktrees, contracts, monitoring) before spinning up agents. The setup time pays for itself immediately.
2. **Flat hierarchy only.** One orchestrator, one layer of sub-agents. If you think you need deeper nesting, decompose the problem differently instead.
3. **Explicit contracts, not implicit expectations.** Every sub-agent gets a written contract with task, input, output format, and constraints. Ambiguity is the enemy of parallelism.
4. **Isolate ruthlessly.** Separate worktrees for separate agents. Containers for autonomous agents. Never let two agents touch the same files.
5. **Merge often, merge early.** Don't let parallel branches diverge too far. Frequent merges keep conflicts small and manageable.

## Attribution

Based on techniques shared at the Coding Agents: AI Driven Dev Conference by Sid (Anthropic) on worktree management and Alfred automation for fast switching, Rob on container isolation and Broomy for managing parallel agents, Harrison Chase (LangChain) on explicit communication contracts for sub-agents, and Niels on keeping agent hierarchies flat at one orchestrator plus one layer of sub-agents.
