---
name: crispi-planning
description: Use when starting a non-trivial coding task, feature, or bug fix that would benefit from upfront planning, research, and structured decomposition before writing code.
---

# CRISPI Planning

## Overview

A multi-stage planning pipeline that separates research, design, and implementation into distinct context windows. Each stage produces a written artifact that feeds the next, preventing context window pollution and ensuring alignment before code is written.

**CRISPI** stands for: **C**ontext, **R**esearch, **I**mplementation design, **S**tructured plan, **I**mplementation.

**Core principle:** Don't use prompts for control flow -- use actual control flow. Each stage runs in a fresh context window with fewer than 40 instructions, producing a document that becomes the input for the next stage.

## When to Use

- Before starting any feature, bug fix, or refactor that touches more than one file
- When a ticket is ambiguous and needs research before you can estimate scope
- When you need alignment with stakeholders before writing code
- When working on unfamiliar parts of the codebase
- When a previous attempt failed due to context window exhaustion

## When NOT to Use

- One-line fixes or typo corrections
- Changes where the implementation is already obvious and self-contained
- Purely mechanical refactors (rename a variable, update an import path)
- When you are already inside an implementation stage with a validated plan

## Common Mistakes

| Mistake | Why it's wrong |
|---------|---------------|
| Combining research and implementation in one context window | Research context pollutes implementation. Separate them so the agent doing research doesn't anchor on a specific solution, and the agent writing code doesn't waste tokens on exploration. (Dex [05:44:35]) |
| Writing a plan that reads like a horizontal layer cake ("first do all the models, then all the routes, then all the tests") | Horizontal plans break at integration boundaries. Build vertically -- one working slice at a time, each independently testable. (Dex [05:58:16]) |
| Skipping the plan and jumping straight to code | "Always start with a plan before coding." The plan is both your roadmap and your recovery mechanism when the context window resets. (Rafael [03:16:14], Sid [00:34:14]) |
| Writing the plan only in your head or in plan mode UI | Write plans to a file (`docs/plan.md` or `docs/plans/`). Files persist across context windows; plan mode state does not. (Rob [03:29:27], Sid [00:41:44]) |
| Letting the plan go stale during implementation | Keep the plan file updated with current task status -- check off completed items, note deviations. It is your context recovery mechanism. (Josh [03:28:11]) |
| Asking the research agent leading questions that reveal your preferred solution | Hide intent from research context. Frame as neutral questions so the agent explores broadly rather than confirming your bias. (Dex [05:44:35]) |

## The Pipeline

```dot
digraph crispi {
  rankdir=LR;
  node [shape=box, style="rounded,filled", fillcolor="#f0f0f0"];

  C [label="1. Context\n(Ticket Decomposition)", fillcolor="#d4e6f1"];
  R [label="2. Research\n(Fresh Window)", fillcolor="#d5f5e3"];
  I1 [label="3. Design Discussion\n(~200 lines)", fillcolor="#fdebd0"];
  S [label="4. Structured Plan\n(Vertical Slices)", fillcolor="#fadbd8"];
  I2 [label="5. Implementation\n(Worktree)", fillcolor="#e8daef"];
  PR [label="6. PR", fillcolor="#d6eaf8"];

  C -> R [label="questions.md"];
  R -> I1 [label="research.md"];
  I1 -> S [label="design.md"];
  S -> I2 [label="plan.md"];
  I2 -> PR [label="code"];
}
```

### Stage 1: Context -- Decompose the Ticket

**Goal:** Turn a vague ticket into specific, answerable research questions.

**Input:** The ticket, issue, or feature request.

**Process:**
1. Read the ticket and any linked documents.
2. Explore the relevant parts of the codebase (`git log`, grep for related files, read existing tests).
3. Decompose the ticket into 3-7 specific research questions. Each question should be answerable independently.
4. Write questions to `docs/plans/questions.md`.

**Output:** `docs/plans/questions.md`

```markdown
# Research Questions for [Ticket Title]

## Questions
1. What is the current data flow from X to Y? Which files are involved?
2. Are there existing patterns in the codebase for handling Z?
3. What are the edge cases around [specific behavior]?
4. Does the current test suite cover [area]? What gaps exist?
5. Are there performance constraints we need to respect?

## Codebase References
- `src/services/foo.ts` -- current implementation of X
- `src/models/bar.ts` -- data model we'll likely modify
```

**Key rule:** Do NOT include your preferred solution in the questions. Frame them neutrally so research is unbiased.

### Stage 2: Research -- Answer the Questions

**Goal:** Gather facts without deciding on an approach.

**Input:** `docs/plans/questions.md` (nothing else -- fresh context window).

**Process:**
1. Open a fresh context. Load only the questions file.
2. For each question, search the codebase, read relevant files, check documentation.
3. Answer each question with facts, code references, and file paths.
4. Note any surprises or constraints discovered during research.
5. Write findings to `docs/plans/research.md`.

**Output:** `docs/plans/research.md`

**Key rule:** This stage is research only. Do not propose solutions. Do not write pseudocode. Just answer the questions.

### Stage 3: Design Discussion -- Align on Approach

**Goal:** Produce a short (~200 line) design document that explores 2-3 approaches and recommends one.

**Input:** `docs/plans/research.md` and `docs/plans/questions.md`.

**Process:**
1. Open a fresh context. Load research and questions.
2. Based on the research findings, propose 2-3 approaches with trade-offs.
3. Recommend one approach with clear reasoning.
4. Include an executive summary at the top (3-5 sentences).
5. Include representative code snippets showing the recommended approach.
6. Write to `docs/plans/design.md`.

**Output:** `docs/plans/design.md` (~200 lines)

```markdown
# Design: [Feature Name]

## Executive Summary
We will [approach] because [reason]. This affects [N] files and
introduces [key concept]. The main risk is [risk] which we mitigate
by [mitigation].

## Approach A: [Name] (Recommended)
[Description with code snippets]

## Approach B: [Name]
[Description with trade-offs]

## Decision
Going with Approach A because [reasons from research].
```

**Key rule:** Get alignment here. This is the cheapest place to change direction. Present this to stakeholders before proceeding.

### Stage 4: Structured Plan -- Vertical Slices

**Goal:** Produce a detailed implementation plan organized as vertical slices, each independently testable.

**Input:** `docs/plans/design.md` and `docs/plans/research.md`.

**Process:**
1. Open a fresh context. Load design and research.
2. Break the approved design into vertical slices. Each slice delivers one working piece of functionality end-to-end.
3. For each slice, list: files to create/modify, functions/signatures to implement, test cases to write, and acceptance criteria.
4. Structure it like a C header file -- show the interfaces and phases without full implementation.
5. Write to `docs/plans/plan.md`.

**Output:** `docs/plans/plan.md` (~2 pages)

```markdown
# Implementation Plan: [Feature Name]

## Status
- [x] Slice 1: Core data model
- [ ] Slice 2: API endpoint  <-- CURRENT
- [ ] Slice 3: UI integration
- [ ] Slice 4: Error handling and edge cases

## Slice 1: Core Data Model
**Files:** `src/models/widget.ts` (new), `src/models/index.ts` (modify)
**Tests:** `src/models/__tests__/widget.test.ts`

Signatures:
- `createWidget(input: WidgetInput): Promise<Widget>`
- `validateWidget(widget: Widget): ValidationResult`

Acceptance criteria:
- Widget can be created with valid input
- Validation rejects [specific invalid cases]

## Slice 2: API Endpoint
...
```

**Key rule:** Vertical, not horizontal. Each slice should be mergeable on its own. Update the status checkboxes as you complete each slice during implementation.

### Stage 5: Implementation -- Execute the Plan

**Goal:** Write the code, slice by slice, using the plan as both roadmap and context recovery.

**Input:** `docs/plans/plan.md`.

**Process:**
1. Open a fresh context (or a git worktree for isolation). Load the plan.
2. Implement one slice at a time. After each slice: run tests, update the plan status, commit.
3. If you hit a problem not covered by the plan, update the plan before continuing.
4. After all slices are complete, do a final review pass.
5. Open a PR.

**Key rule:** When your context window resets mid-implementation, reload `docs/plans/plan.md`. The status checkboxes tell you exactly where you left off.

## Quick Reference

| Item | Location |
|------|----------|
| Research questions | `docs/plans/questions.md` |
| Research findings | `docs/plans/research.md` |
| Design discussion | `docs/plans/design.md` |
| Implementation plan | `docs/plans/plan.md` |
| Plan status tracking | Checkboxes in `plan.md` |
| Named plan alternative | `docs/plans/YYYY-MM-DD-<topic>-plan.md` |

## Key Principles

1. **Each stage gets a fresh context window.** Don't carry research tokens into implementation. Each stage reads the previous stage's document and nothing more.
2. **Every stage produces a file, not a conversation.** Files persist across context resets. Conversation history does not. The plan file is your context recovery mechanism.
3. **Vertical slices, not horizontal layers.** Build one working end-to-end slice before starting the next. Each slice is independently testable and mergeable.
4. **Research and implementation are separate concerns.** Hide your solution intent from the research stage. Let facts drive design, not the reverse.
5. **Keep the plan alive.** Update status checkboxes, note deviations, add discovered edge cases. A stale plan is worse than no plan -- it gives false confidence.
6. **Under 40 instructions per stage.** If a stage's prompt is growing beyond 40 lines of instruction, you are combining stages. Split it.

## Attribution

Based on techniques shared at the Coding Agents: AI Driven Dev Conference. The CRISPI pipeline draws primarily from Dex (HumanLayer) who presented the full Questions -> Research -> Design -> Structure -> Plan -> Worktree -> Implement -> PR pipeline [05:44:35 - 06:01:43], including the critical insight of separating research from implementation intent. Plan-as-context-recovery comes from Sid (Anthropic) [00:34:14, 00:41:44] who advocated extensive plan mode use and checking plans into `docs/`. The "always start with a plan" principle comes from Rafael [03:16:14] who stressed including code snippets and executive summaries. File-based plans over built-in plan mode was advocated by Rob [03:29:27], and keeping the plan updated with task status was emphasized by Josh [03:28:11].
