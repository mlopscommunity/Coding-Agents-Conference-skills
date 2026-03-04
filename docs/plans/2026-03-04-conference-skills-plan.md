# Conference Skills Extraction Plan

**Source**: Coding Agents: AI Driven Dev Conference (6h 45m, 1159 paragraphs)
**Goal**: Extract actionable insights from the conference transcript and turn them into shareable Claude Code skills for conference attendees.
**Status**: All 12 skills complete — packaging for distribution

---

## Executive Summary

The conference transcript contains ~40+ actionable insights from speakers including Sid (Anthropic/Claude Code team), Dex (HumanLayer), Scott (Kilo), Harrison Chase (LangChain), Faye Zhang (Pinterest), Ankit (Databricks), Rob, Josh, and others. These cluster into 12 skill categories. This document tracks what was found, what skills to build, and progress on each.

---

## Skill Categories & Extracted Insights

### 1. CRISPI Planning Workflow
**Speakers**: Dex (HumanLayer), Sid (Anthropic)
**Skill Status**: [x] Complete

The single most detailed workflow from the conference. Evolved from "Research, Plan, Implement" (RPI) into a multi-stage pipeline with strict context isolation.

**Insights**:
- [x] Use plan mode extensively; check plans into `docs/` folder (Sid [00:34:14])
- [x] Plan files as context window recovery mechanism (Sid [00:41:44])
- [x] Always start with a plan before coding; include code snippets + executive summary (Rafael [03:16:14])
- [x] Write plans to `plan.md` instead of using built-in plan mode (Rob [03:29:27])
- [x] Keep plan file updated with current task status (Josh [03:28:11])
- [x] Separate research from the ticket — hide intent from research context (Dex [05:44:35])
- [x] Decompose tickets into specific research questions (Dex [05:45:02])
- [x] Full pipeline: Questions -> Research -> Design Discussion -> Structure Outline -> Plan -> Worktree -> Implement -> PR (Dex [06:01:43])

---

### 2. Context Window Management
**Speakers**: Dex (HumanLayer), Josh, Harrison Chase (LangChain)
**Skill Status**: [x] Complete

Practical heuristics for when to clear context, how to manage instruction budgets, and how to keep context lean.

**Insights**:
- [x] Mind instruction budget: ~150-200 max across all sources (Dex [05:47:53])
- [x] Keep individual prompts under 40 instructions (Dex [05:53:38])
- [x] Don't use prompts for control flow — use actual control flow (Dex [05:53:38])
- [x] Context under 40% for beginners; 60% max for experienced users (Dex [06:06:24])
- [x] Offload large tool results to files, show first ~100 lines (Harrison Chase [06:16:33])
- [x] More context is not always better — clear and restart when confused (Josh [03:27:28])
- [x] Save important state to static markdown artifacts, not context window (Dex [06:06:24])

---

### 3. Adversarial Code Review
**Speakers**: Sid (Anthropic), Chad, Ankit (Databricks)
**Skill Status**: [x] Complete

Multi-agent review patterns with confidence thresholds, cross-model review, and noise reduction.

**Insights**:
- [x] Run adversarial agents: one builds, another critiques, a third critiques the review (Sid [00:23:56])
- [x] CI-integrated review with `--append-system-prompt` and adversarial sub-agents (Sid [00:30:31])
- [x] Reduce review noise to ~2 high-priority, high-confidence comments per PR (Sid [00:42:56])
- [x] Use a different model for review than for writing (Ankit/Databricks [05:17:41])
- [x] Trick: tell reviewer "Codex just introduced bugs, go find them" to prime criticality (Demetrios [00:32:07])

---

### 4. Hooks & Enforcement
**Speakers**: Josh, Yari, Sid (Anthropic), Milan (Semgrep)
**Skill Status**: [x] Complete

Using Claude Code hooks to enforce what CLAUDE.md alone cannot.

**Insights**:
- [x] Pre-commit hooks preferred over per-edit hooks — less disruptive to flow (Sid [00:38:04])
- [x] Use lifecycle hooks to enforce linting, tests, compilation (Josh [03:26:20])
- [x] LLM-powered auto-approval hook for permission prompts (Yari [03:23:10])
- [x] Create "immutable tests" the agent cannot modify (Josh [03:28:41])
- [x] Set up audit trail hooks — log every shell command with timestamp (Milan/Semgrep [05:03:20])
- [x] Scan agent-generated code with security tools before shipping (Milan/Semgrep [05:05:11])

---

### 5. Parallel Agent Management
**Speakers**: Sid (Anthropic), Rob, Harrison Chase (LangChain), Niels
**Skill Status**: [x] Complete

Managing multiple agents across worktrees, containers, and sub-agent architectures.

**Insights**:
- [x] Five predefined worktrees + Alfred/AppleScript automation for switching (Sid [00:25:37])
- [x] Use Broomy or similar for managing parallel agents across worktrees (Rob [03:18:39])
- [x] Run agents in containers to safely use `--dangerously-skip-permissions` (Rob [03:22:46])
- [x] Sub-agents need explicit communication contracts — be specific about task and return format (Harrison Chase [06:15:44])
- [x] One main agent + one layer of sub-agents is sufficient for most cases (Niels [02:09:14])

---

### 6. Objective Research Technique
**Speakers**: Dex (HumanLayer)
**Skill Status**: [x] Complete

Keeping codebase research factual by separating intent from investigation.

**Insights**:
- [x] Hide the ticket from the research agent — use separate context windows (Dex [05:44:35])
- [x] One context generates research questions from the ticket; a fresh context executes the research (Dex [05:44:35])
- [x] Decompose tickets into specific, targeted research questions that trace code paths (Dex [05:45:02])

---

### 7. Skills as Expert Personas
**Speakers**: Rafael, Sid (Anthropic), Josh
**Skill Status**: [x] Complete

Creating lightweight skills that prime the agent with domain expertise.

**Insights**:
- [x] Skills don't need to be long — even 40 lines can activate latent knowledge (Rafael [03:37:46])
- [x] Create skills for non-coding domains: trademarks, go-to-market, PM, security (Rafael [03:37:46])
- [x] Use well-executed open source projects as design references for unfamiliar domains (Josh [03:41:29])
- [x] Skills = bags of context + MCP servers; everything else is boilerplate (Sid [00:22:49])

---

### 8. Visual Regression Testing
**Speakers**: Rob
**Skill Status**: [x] Complete — `skills/visual-regression/SKILL.md`

Automated screenshot-based QA at release time.

**Insights**:
- [x] Agent creates Playwright screenshot walkthroughs for every user-facing change (Rob [03:20:25])
- [x] At release: screenshot old tag, screenshot new tag, pixel diff, sub-agent analyzes expected vs unexpected changes (Rob [03:20:25])
- [x] Run on separate build box at release time, NOT in CI (too slow) (Rob [03:22:07])

---

### 9. Voice-First Planning
**Speakers**: Josh
**Skill Status**: [x] Complete

Using voice dictation for richer initial specs.

**Insights**:
- [x] Use WhisperFlow or similar to speak initial specs — speaking gives more context than typing (Josh [03:31:42])
- [x] LLMs are good at extracting meaning from rambling speech (Josh [03:31:42])
- [x] Use TMUX + VIM mode for quick editing of transcription errors (Josh [03:34:22])

---

### 10. Agent-Maintained Documentation
**Speakers**: Rob
**Skill Status**: [x] Complete

Having agents keep documentation current with validation hooks.

**Insights**:
- [x] Add documentation comments to top of every file + README per folder (Rob [03:42:50])
- [x] Use a validation skill at commit time to ensure docs stay current (Rob [03:43:18])
- [x] Agents maintain docs reliably if enforced; humans don't (Rob [03:43:30])

---

### 11. Three-Layer Memory System
**Speakers**: audience member
**Skill Status**: [x] Complete

Layered memory architecture across tools.

**Insights**:
- [x] Layer 1: Memory MCP (cross-app, Claude Desktop + Claude Code) ([03:52:56])
- [x] Layer 2: Claude Code auto-memory (per-repo `.claude/memory/`) ([03:52:56])
- [x] Layer 3: External markdown editor (Joplin/Obsidian) as research library ([03:52:56])
- [x] Configure CLAUDE.md to tell agent when to use each tier ([03:55:03])

---

### 12. Product Research with Agents
**Speakers**: Rob, Omeh
**Skill Status**: [x] Complete

Using agents for open-ended competitor/customer/market research.

**Insights**:
- [x] Give Claude Code big open-ended research questions; brain-dump all open questions (Rob [03:35:29])
- [x] Use deep research tools (Perplexity, ChatGPT) first to save tokens, then feed plan to Claude (Omeh [03:44:15])
- [x] Agent can surface competitor weaknesses, customer org charts, stakeholder info (Rob [03:37:04])

---

## Bonus Insights (Not Full Skill Categories)

### Quick Remediation > Proactive Bug Prevention
- Ship faster, fix faster. The Claude Code team ran with no branch protections initially. (Sid [00:45:03])

### Architecture Review as the Human Leverage Point
- Focus human review only on architecture; TDD agent writes tests, coder implements, reviewer checks alignment. If tests pass, ship. (Tevye [03:49:05])

### Iterative Critique Loop for Plans
- Versioned critique cycle: plan_v1 -> critique_opus_v1 + critique_gpt_v1 -> revise -> plan_v2. Repeat until convergence. (Chad [03:46:12])

### Agent Therapist Mode
- Ask questions instead of giving commands — gives agent room for creativity and critique. (Chubo [03:49:52])

### Right Model for Right Task
- Frontier models for architecture; cheaper models for coding/debugging. (Scott/Kilo [00:59:42])

### Cross-Repo Context
- Give agents access to related repos, not just the one being edited. (Scott/Kilo [00:57:46])

### Scrap and Restart
- Don't be precious — starting over from a plan is often faster than debugging a confused session. (Josh [03:27:28])

### Minimize MCP Server Connections
- Don't enable all MCPs — floods context with tool descriptions. Only connect what's needed. (Ankit/Databricks [05:30:40])

### Checkpoint-Based Recovery
- Replay logs for crash recovery — record every tool call, resume from last successful step. (Niels [02:06:07])

### Secrets Management
- Never put API keys in env vars for MCP servers. Use a proper secret store. (Sam Partee/Arcade [06:23:55])

---

## Task Tracking

### Phase 1: Planning
- [x] Extract insights from transcript
- [x] Organize into skill categories
- [x] Create this plan document
- [x] Decide which skills to build first — all 12
- [x] Decide skill format and structure — based on visual-regression reference
- [x] Write parallel execution plan (`docs/plans/2026-03-04-parallel-skill-creation.md`)

### Phase 2: Skill Creation (Parallel)
- [x] Skill 1: Visual Regression Testing (`skills/visual-regression/SKILL.md`)
- [x] Skill 2: CRISPI Planning Workflow (`skills/crispi-planning/SKILL.md`)
- [x] Skill 3: Context Window Management (`skills/context-window-management/SKILL.md`)
- [x] Skill 4: Adversarial Code Review (`skills/adversarial-code-review/SKILL.md`)
- [x] Skill 5: Hooks & Enforcement (`skills/hooks-and-enforcement/SKILL.md`)
- [x] Skill 6: Parallel Agent Management (`skills/parallel-agent-management/SKILL.md`)
- [x] Skill 7: Objective Research (`skills/objective-research/SKILL.md`)
- [x] Skill 8: Expert Persona Skills (`skills/expert-persona-skills/SKILL.md`)
- [x] Skill 9: Voice-First Planning (`skills/voice-first-planning/SKILL.md`)
- [x] Skill 10: Agent-Maintained Docs (`skills/agent-maintained-docs/SKILL.md`)
- [x] Skill 11: Three-Layer Memory (`skills/three-layer-memory/SKILL.md`)
- [x] Skill 12: Product Research (`skills/product-research/SKILL.md`)

### Phase 3: Packaging & Distribution
- [x] Merge all worktree branches — N/A (all created on main branch)
- [x] Update plan document with all completions
- [ ] Create README with installation instructions
- [ ] Package for distribution to conference attendees
