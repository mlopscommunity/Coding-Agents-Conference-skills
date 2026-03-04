# Parallel Skill Creation Plan

> **For Claude:** Use superpowers:dispatching-parallel-agents to execute this plan. Each task is independent and can run in a separate worktree or subagent.

**Goal:** Create all 11 remaining Claude Code skills from the conference transcript insights, in parallel.

**Architecture:** Each skill is independent — no dependencies between them. Each agent gets: the conference insights for that skill (from the plan doc), the visual-regression skill as a format reference, and the writing-skills methodology. Each agent follows RED-GREEN-REFACTOR: baseline test without skill, write skill, test with skill.

**Output:** Each agent produces one `skills/<skill-name>/SKILL.md` file.

---

## Shared Context for All Agents

Every agent needs these inputs:

1. **Format reference**: Read `skills/visual-regression/SKILL.md` for the proven structure (YAML frontmatter, Overview, When to Use, When NOT to Use, Common Mistakes, step-by-step technique, Quick Reference, Key Principles, Attribution)
2. **Conference insights**: The specific insights listed below for each skill
3. **Writing methodology**: Follow RED-GREEN-REFACTOR — run a baseline scenario without the skill, identify gaps, write skill addressing those gaps, test with skill loaded
4. **Skill constraints**: Description starts with "Use when...", no workflow summary in description, under 500 words for description, technique skills focus on application not discipline

---

## Task 1: CRISPI Planning Workflow

**Skill name:** `crispi-planning`
**Directory:** `skills/crispi-planning/SKILL.md`

**Conference insights to encode:**
- Use plan mode extensively; check plans into `docs/` folder (Sid [00:34:14])
- Plan files as context window recovery mechanism (Sid [00:41:44])
- Always start with a plan before coding; include code snippets + executive summary (Rafael [03:16:14])
- Write plans to `plan.md` instead of using built-in plan mode (Rob [03:29:27])
- Keep plan file updated with current task status (Josh [03:28:11])
- Separate research from the ticket — hide intent from research context (Dex [05:44:35])
- Decompose tickets into specific research questions (Dex [05:45:02])
- Full pipeline: Questions -> Research -> Design Discussion -> Structure Outline -> Plan -> Worktree -> Implement -> PR (Dex [06:01:43])
- Design discussion doc (~200 lines) for alignment before full plan (Dex [05:55:30])
- Structure outline (~2 pages, like C header files) showing phases and signatures (Dex [05:57:14])
- Vertical plans over horizontal plans — build slice by slice (Dex [05:58:16])

**Key principle:** Each stage uses a fresh context window with <40 instructions. Don't use prompts for control flow — use actual control flow.

**Baseline test prompt:** "I have a ticket to add a new API endpoint with frontend integration. Help me plan the implementation."

---

## Task 2: Context Window Management

**Skill name:** `context-window-management`
**Directory:** `skills/context-window-management/SKILL.md`

**Conference insights to encode:**
- Mind instruction budget: ~150-200 max across all sources (Dex [05:47:53])
- Keep individual prompts under 40 instructions (Dex [05:53:38])
- Don't use prompts for control flow — use actual control flow (Dex [05:53:38])
- Context under 40% for beginners; 60% max for experienced users (Dex [06:06:24])
- Offload large tool results to files, show first ~100 lines (Harrison Chase [06:16:33])
- More context is not always better — clear and restart when confused (Josh [03:27:28])
- Save important state to static markdown artifacts, not context window (Dex [06:06:24])

**Key principle:** Less context = better results. Save state to files, not memory.

**Baseline test prompt:** "My Claude Code session is getting slow and the agent seems confused. I've been going back and forth for a while. What should I do?"

---

## Task 3: Adversarial Code Review

**Skill name:** `adversarial-code-review`
**Directory:** `skills/adversarial-code-review/SKILL.md`

**Conference insights to encode:**
- Run adversarial agents: one builds, another critiques, a third critiques the review (Sid [00:23:56])
- CI-integrated review with `--append-system-prompt` and adversarial sub-agents (Sid [00:30:31])
- Reduce review noise to ~2 high-priority, high-confidence comments per PR (Sid [00:42:56])
- Use a different model for review than for writing (Ankit/Databricks [05:17:41])
- Trick: tell reviewer "Codex just introduced bugs, go find them" to prime criticality (Demetrios [00:32:07])
- Versioned critique cycle: plan_v1 -> critique_opus_v1 + critique_gpt_v1 -> revise -> plan_v2 (Chad [03:46:12])

**Key principle:** Fewer, higher-quality review comments build trust. High confidence + high priority only.

**Baseline test prompt:** "I want to set up automated code review for my team's PRs using Claude Code. How should I approach this?"

---

## Task 4: Hooks & Enforcement

**Skill name:** `hooks-and-enforcement`
**Directory:** `skills/hooks-and-enforcement/SKILL.md`

**Conference insights to encode:**
- Pre-commit hooks preferred over per-edit hooks — less disruptive to flow (Sid [00:38:04])
- Use lifecycle hooks to enforce linting, tests, compilation (Josh [03:26:20])
- LLM-powered auto-approval hook for permission prompts (Yari [03:23:10])
- Create "immutable tests" the agent cannot modify (Josh [03:28:41])
- Set up audit trail hooks — log every shell command with timestamp (Milan/Semgrep [05:03:20])
- Scan agent-generated code with security tools before shipping (Milan/Semgrep [05:05:11])

**Key principle:** Instructions in CLAUDE.md are suggestions; hooks are enforcement. Use hooks for anything that MUST happen.

**Baseline test prompt:** "I put 'always run tests before committing' in my CLAUDE.md but Claude keeps skipping it. How do I enforce this?"

---

## Task 5: Parallel Agent Management

**Skill name:** `parallel-agent-management`
**Directory:** `skills/parallel-agent-management/SKILL.md`

**Conference insights to encode:**
- Five predefined worktrees + Alfred/AppleScript automation for switching (Sid [00:25:37])
- Use Broomy or similar for managing parallel agents across worktrees (Rob [03:18:39])
- Run agents in containers to safely use `--dangerously-skip-permissions` (Rob [03:22:46])
- Sub-agents need explicit communication contracts — be specific about task and return format (Harrison Chase [06:15:44])
- One main agent + one layer of sub-agents is sufficient for most cases (Niels [02:09:14])
- Keep 5-10 Claude Code web sessions for random ideas throughout the day (Sid [00:27:07])

**Key principle:** The bottleneck with parallel agents is organization, not capability. Invest in the scaffolding.

**Baseline test prompt:** "I want to run multiple Claude Code agents on different features at the same time. How do I set this up?"

---

## Task 6: Objective Research

**Skill name:** `objective-research`
**Directory:** `skills/objective-research/SKILL.md`

**Conference insights to encode:**
- Hide the ticket from the research agent — use separate context windows (Dex [05:44:35])
- One context generates research questions from the ticket; a fresh context executes the research (Dex [05:44:35])
- Decompose tickets into specific, targeted research questions that trace code paths (Dex [05:45:02])
- Research should be purely factual — compressed truth about how the code works today (Dex [05:45:33])

**Key principle:** If the research agent knows what you're building, it injects opinions into facts. Separate intent from investigation.

**Baseline test prompt:** "I need to understand how authentication works in this codebase before I add a new auth method. How should I research this?"

---

## Task 7: Expert Persona Skills

**Skill name:** `expert-persona-skills`
**Directory:** `skills/expert-persona-skills/SKILL.md`

**Conference insights to encode:**
- Skills don't need to be long — even 40 lines can activate latent knowledge (Rafael [03:37:46])
- Create skills for non-coding domains: trademarks, go-to-market, PM, security (Rafael [03:37:46])
- Use well-executed open source projects as design references for unfamiliar domains (Josh [03:41:29])
- Skills = bags of context + MCP servers; everything else is boilerplate (Sid [00:22:49])
- The built-in "frontend design" skill is only ~40 lines (Rafael [03:37:46])

**Key principle:** You're not teaching the LLM — you're activating knowledge it already has. Short, focused priming beats long instruction sets.

**Baseline test prompt:** "I want to create a Claude Code skill that makes the agent an expert in my domain. How should I structure it?"

---

## Task 8: Voice-First Planning

**Skill name:** `voice-first-planning`
**Directory:** `skills/voice-first-planning/SKILL.md`

**Conference insights to encode:**
- Use WhisperFlow or similar to speak initial specs — speaking gives more context than typing (Josh [03:31:42])
- LLMs are good at extracting meaning from rambling speech (Josh [03:31:42])
- Use TMUX + VIM mode for quick editing of transcription errors (Josh [03:34:22])
- Especially effective during the planning/ideation stage, not during implementation (Josh [03:31:42])

**Key principle:** Speaking freely captures intent that's hard to express in typed text. Don't self-edit — ramble and let the LLM find the structure.

**Baseline test prompt:** "I have a complex feature idea but I'm struggling to write it out as a prompt. Any tips for getting my ideas into Claude Code more effectively?"

---

## Task 9: Agent-Maintained Documentation

**Skill name:** `agent-maintained-docs`
**Directory:** `skills/agent-maintained-docs/SKILL.md`

**Conference insights to encode:**
- Add documentation comments to top of every file + README per folder (Rob [03:42:50])
- Use a validation skill at commit time to ensure docs stay current (Rob [03:43:18])
- Agents maintain docs reliably if enforced; humans don't (Rob [03:43:30])
- This helps agents (and humans) navigate the codebase via grep/search (Rob [03:42:50])

**Key principle:** Documentation is a codebase navigation tool for agents. Enforce updates with hooks, because agents will actually maintain docs — humans won't.

**Baseline test prompt:** "My codebase is hard for Claude to navigate — it keeps looking at the wrong files. How can I make it more navigable?"

---

## Task 10: Three-Layer Memory

**Skill name:** `three-layer-memory`
**Directory:** `skills/three-layer-memory/SKILL.md`

**Conference insights to encode:**
- Layer 1: Memory MCP (cross-app, Claude Desktop + Claude Code) ([03:52:56])
- Layer 2: Claude Code auto-memory (per-repo `.claude/memory/`) ([03:52:56])
- Layer 3: External markdown editor (Joplin/Obsidian) as research library ([03:52:56])
- Configure CLAUDE.md to tell agent when to use each tier ([03:55:03])

**Key principle:** Different types of knowledge belong in different memory tiers. Cross-tool global memory, per-project auto-memory, and an external knowledge base for research artifacts.

**Baseline test prompt:** "I keep re-explaining the same things to Claude Code across sessions. How do I set up a memory system?"

---

## Task 11: Product Research with Agents

**Skill name:** `product-research`
**Directory:** `skills/product-research/SKILL.md`

**Conference insights to encode:**
- Give Claude Code big open-ended research questions; brain-dump all open questions (Rob [03:35:29])
- Use deep research tools (Perplexity, ChatGPT) first to save tokens, then feed plan to Claude (Omeh [03:44:15])
- Agent can surface competitor weaknesses, customer org charts, stakeholder info (Rob [03:37:04])
- Treat it like having 100 researchers — dump all your open questions stream-of-consciousness (Rob [03:35:42])

**Key principle:** Claude Code with web access can do powerful product research if you give it broad, open questions. Offload deep research to cheaper tools first.

**Baseline test prompt:** "I want to understand what my competitors are doing and what my users need. Can Claude Code help with product research?"

---

## Execution Instructions

### For each task, the agent must:

1. **Read** `skills/visual-regression/SKILL.md` as the format reference
2. **RED phase**: Run the baseline test prompt WITHOUT the skill — document what the agent gets wrong or misses
3. **GREEN phase**: Write the `SKILL.md` addressing the baseline gaps
4. **Test**: Run the same prompt WITH the skill loaded — verify improvement
5. **Commit**: `git add skills/<name>/SKILL.md && git commit -m "Add <name> skill"`
6. **Update plan**: Mark the skill as complete in `docs/plans/2026-03-04-conference-skills-plan.md`

### Parallel execution strategy:

All 11 tasks are fully independent. They can run simultaneously in separate worktrees or subagents. No task depends on another task's output.

### After all tasks complete:

1. Merge all worktree branches
2. Update the plan document with all completions
3. Create a README.md with installation instructions
4. Package for distribution to conference attendees
