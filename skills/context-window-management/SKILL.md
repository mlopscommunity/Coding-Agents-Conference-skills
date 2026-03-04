---
name: context-window-management
description: Use when working on multi-step tasks, long conversations, or when agent output quality degrades mid-session. Techniques for keeping context lean so the model produces better results.
---

# Context Window Management

## Overview

Techniques for managing what goes into the context window so the model stays focused and produces high-quality output. The core insight is counterintuitive: **less context produces better results**. Stuffing the context window with everything available degrades performance. Instead, save state to files, keep prompts short, and restart sessions when confused.

**Core principle:** The context window is expensive working memory, not cheap storage. Offload state to files and load only what you need right now.

## When to Use

- At the start of any multi-step implementation (plan your context budget before you begin)
- When agent output quality drops mid-conversation (hallucinations, repetition, ignoring instructions)
- When combining multiple prompt sources (system prompt, CLAUDE.md, tool results, user instructions)
- When tool calls return large payloads (logs, file contents, API responses)
- When a task requires more than 3-4 back-and-forth exchanges

## When NOT to Use

- Single-shot questions with short answers
- Tasks that genuinely need the full context loaded (e.g., cross-file refactors where all files fit comfortably)
- When you are already under 40% context utilization

## Common Mistakes

| Mistake | Why it's wrong |
|---------|---------------|
| Dumping entire file contents into context | Large tool results push out earlier instructions. Offload to a file and show only the first ~100 lines. Harrison Chase: "Load the first hundred lines, let the agent ask for more." |
| Writing 50+ instructions in a single prompt | The model starts dropping instructions past ~40. Dex: "Keep individual prompts under 40 instructions." Budget across all sources. |
| Using the system prompt for control flow logic | Prompts are for goals and constraints, not if/else branching. Use actual code for control flow. Dex: "Don't use prompts for control flow -- use actual control flow." |
| Continuing a confused conversation instead of restarting | Accumulated confusion compounds. Josh: "Clear and restart when confused. More context is not always better." |
| Treating the context window as a notebook | Important state belongs in static markdown files on disk, not carried in the conversation. Context is volatile; files are persistent. |
| Ignoring total instruction count across sources | Your system prompt, CLAUDE.md, tool descriptions, and user message all share one budget of ~150-200 instructions max. Going over means something gets silently dropped. |

## Technique: Context Budget Planning

### Step 1: Audit your instruction sources

Before starting work, count the instructions the model will receive from all sources combined:

- **System prompt / custom instructions**: How many directives?
- **Project instructions (CLAUDE.md, etc.)**: How many rules?
- **Tool descriptions**: Each tool schema counts against the budget.
- **User message**: How many asks in this turn?

**Target total: under 150-200 instructions across all sources.** If you are over, cut the lowest-priority instructions. No single source should exceed 40 instructions.

### Step 2: Set your context utilization target

| Experience level | Max context utilization | Why |
|-----------------|------------------------|-----|
| Beginner / unfamiliar codebase | 40% | Leave headroom for mistakes and recovery |
| Experienced / familiar codebase | 60% | You can be more precise about what to include |

Never target higher than 60%. The remaining space is needed for the model's own reasoning and output generation.

### Step 3: Offload large results to files

When a tool call returns a large result (file contents, logs, API responses):

1. Write the full result to a temporary file (e.g., `docs/scratch/tool-output-<timestamp>.md`).
2. Show only the first ~100 lines in the conversation.
3. Reference the file path so the agent can read more if needed.

```
# Instead of pasting 2000 lines of logs:
[First 100 lines of build output shown]
Full output saved to: docs/scratch/build-output-2026-03-04.log
```

### Step 4: Save state to markdown artifacts

At natural breakpoints in a multi-step task, write the current state to a markdown file:

- What has been completed
- What remains
- Key decisions made and why
- File paths modified

Save to `docs/scratch/` or a similar scratch directory. This lets you restart the conversation fresh while preserving progress.

### Step 5: Recognize when to clear and restart

Signs the context window is degraded:

- The model repeats itself or contradicts earlier statements
- Instructions you gave earlier are being ignored
- The model hallucinates file contents or tool outputs
- Output quality is noticeably worse than at the start of the conversation

When this happens: **save state to a file and start a new session.** Load only the state file and the next task. Do not try to "remind" the model -- a fresh start with less context will outperform a long conversation every time.

### Step 6: Structure prompts for the budget

When writing instructions (system prompts, CLAUDE.md, project rules):

- **Under 40 instructions per source.** This is the reliable ceiling for a single prompt.
- **Use actual control flow for branching logic.** If you find yourself writing "If X, do Y; otherwise do Z" in a prompt, move that logic into code that selects which prompt to send.
- **Front-load the most important instructions.** The model pays more attention to what comes first.
- **Delete instructions that duplicate tool descriptions.** If a tool's schema already describes its behavior, don't repeat it in prose.

## Quick Reference

| Threshold | Value | Source |
|-----------|-------|--------|
| Max instructions per prompt | ~40 | Dex |
| Max total instructions (all sources) | ~150-200 | Dex |
| Beginner context utilization target | 40% | Dex |
| Experienced context utilization target | 60% max | Dex |
| Large tool result preview | First ~100 lines | Harrison Chase |
| Signs of degradation | Repetition, hallucination, ignored instructions | Josh |
| Recovery action | Save state to file, restart session | Josh, Dex |

## Key Principles

1. **Less context = better results.** This is the single most important insight. Resist the urge to "give the model everything." Curate ruthlessly.
2. **The context window is working memory, not storage.** Use files for storage. Load into context only what the current step requires.
3. **Budget instructions across all sources.** System prompt + project rules + tool schemas + user message all share one pool of ~150-200 instructions. Exceeding this means silent drops.
4. **No single prompt over 40 instructions.** Past this point, compliance drops. Split into multiple interactions or move logic to code.
5. **Save state, restart often.** A fresh session with a state file beats a long degraded conversation. Make "save and restart" a habit, not a last resort.
6. **Don't use prompts for control flow.** Prompts set goals and constraints. Code handles branching. Mixing the two wastes context and confuses the model.

## Attribution

Based on techniques from the Coding Agents: AI Driven Dev Conference. Key contributors: Dex (HumanLayer) on instruction budgets, prompt sizing, and context utilization thresholds; Harrison Chase (LangChain) on offloading large tool results to files; and Josh on recognizing context degradation and the practice of clearing and restarting sessions.
