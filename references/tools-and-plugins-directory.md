# Tools & Plugins Directory

A curated reference of tools, plugins, and services used across modern AI-driven coding workflows. All entries include real-world context from practitioner feedback.

---

## AI Coding Agents & IDEs

### Claude Code
**What it does:** Anthropic's terminal-based coding agent; primary tool for automated development workflows.
**Key features:** Raw speed, deep context understanding, skill composition
**Tips:** Use as your primary terminal (Rahul). Pair with validation sub-agents for complex tasks. Native integration with Claude's latest models.

### Cursor
**What it does:** IDE with integrated AI, custom plan mode auto-switching, multi-agent competition support
**Key features:** Visual editing, multi-file preview, conditional rule loading per workspace
**Tips:** Auto-switches into plan mode (unlike Claude). Good for developers who want visual feedback while agents work. Supports parallel agent patterns.

### Broomy/Brumi (Rob Ennals)
**What it does:** Custom IDE for managing parallel agent sessions; sits on top of Claude Code/Cursor/Gemini
**Key features:** Session status visibility, customizable command buttons, orchestration layer for multi-agent workflows
**Tips:** Solves cognitive overload when running 2-3 agents in parallel. Keeps you in "work mode" instead of manual context switching.

### VS Code + Copilot
**What it does:** IDE integration with Microsoft's copilot
**Tips:** Standard industry baseline; useful for developers accustomed to VSCode ecosystem

### Gemini CLI
**What it does:** Google's command-line agent interface
**Tips:** Available as alternative to Claude Code; less adoption in production workflows

### Codex (OpenAI)
**What it does:** Legacy OpenAI code model
**Tips:** Mentioned primarily for historical comparison; mostly superseded by newer models

---

## Model Context Protocol (MCP)

MCPs extend agent context with specialized tools. Key limitation: each adds to token budget.

### Datadog MCP
**What it does:** Metrics analysis, profiling, notebooks, dashboards integration
**Who loves it:** Tristan E (essential for observability-heavy workflows)
**Tip:** Connect live production metrics to your agent's reasoning loop

### Playwright MCP
**What it does:** UI testing automation and browser interaction
**Used in:** "Punch It" skill for automated browser testing workflows
**Tip:** Critical for end-to-end validation in web development

### Drata MCP
**What it does:** SOC 2 compliance automation
**Warning:** Leo cautions that this was "lazily ported with 75 tools" — floods context window badly
**Tip:** If using Drata, create an abstraction layer that maps 75 endpoints to 3-5 high-level functions

### Tailwind MCP
**What it does:** Documentation access for Tailwind CSS
**Tip:** Lightweight; good for frontend-heavy projects

### GitHub MCP
**What it does:** Repository searching, bug identification, PR management
**Tip:** Essential for multi-repo analysis and issue tracking

---

## Plugins

Plugins extend Claude's native capabilities through the marketplace.

### Linear Plugin
**What it does:** Issue tracking and sprint planning integration
**Mentioned by:** Rahul (Part/Plan/Build/Punch It workflow)
**Tip:** Ties agent work directly to team task management; enables automated issue closure

### Superpowers Git Plugin
**What it does:** Automatically suggests when to use sub-agents, team creation and delegation
**Mentioned by:** Justin Kellam
**Tip:** Bridges the gap between solo agent work and team-scale orchestration

---

## Custom Skills

Skills are reusable workflows composed into Claude Code. All below are actively used in production.

### Brainstorming Skill
**What it does:** Rigorous plan clarification with structured follow-up questions
**Created by:** Demetrios
**Tip:** Use before starting big tasks to avoid scope creep and direction changes

### Playground Skill
**What it does:** Visual debugging, architecture mapping, UI design with interactive sliders/color pickers
**Created by:** Demetrios
**Tip:** Bridges the "bug explanation gap" — generates hyperspecific prompts with code snippets when agents struggle to describe issues

### Claude Ception
**What it does:** Self-learning skill that creates new skills after completing tasks
**Created by:** Demetrios
**Tip:** Experimental but powerful for iterative refinement; enables skills to evolve from experience

### Create Skill
**What it does:** Template for organizing and scaffolding new skills
**Created by:** Rahul
**Tip:** Use this as the foundation when building custom skills for your team

### Plan/Build/Punch It
**What it does:** Three-phase development workflow (planning → implementation → validation/testing)
**Created by:** Rahul
**Integration:** Tied directly to Linear for task tracking
**Tip:** Scale-tested pattern for shipping production code with agent automation

---

## Terminals & Development Environments

### Alacrity
**What it does:** Terminal emulator with custom scripting
**Extensions used:** Custom scripts for branch info, token usage tracking
**Used by:** Justin Kellam
**Tip:** Pairs well with Claude Code for raw speed workflows; enables real-time feedback on agent costs

---

## Evaluation & Observability Platforms

These platforms evaluate agent quality, cost, and reliability across tasks.

### LangSmith
**What it does:** Evaluation platform built on Langchain ecosystem
**Use case:** Evals for LLM chains and workflows
**Tip:** Good integration if you're already in Langchain ecosystem

### Fireworks AI
**What it does:** Out-of-the-box evaluation tools with inference optimization
**Use case:** Quick eval setup without heavy instrumentation
**Tip:** Lightweight alternative to full observability stacks

### Weights & Biases
**What it does:** ML evaluation and experiment tracking platform
**Use case:** Team-scale evals and model comparison
**Tip:** Strongest for teams doing systematic benchmarking

### Phoenix
**What it does:** Observability and evaluation for LLM applications
**Use case:** Trace-based debugging and quality metrics
**Tip:** Good for detecting context degradation in long-running projects

### Scale AI
**What it does:** Data labeling and benchmark creation
**Notable:** Presented SWE Bench Atlas (124 tasks for code quality evaluation)
**Tip:** Use for creating golden datasets when building custom eval metrics

---

## Benchmarks & Standards

### SWE Bench Atlas
**What it does:** 124 software engineering tasks covering code Q&A, test writing, refactoring
**Features:** Includes confidence intervals, systematic task organization
**Tip:** Use smaller samples (5-20-100) for iteration speed; full benchmark for final validation

### SWE Bench MCP Atlas
**What it does:** Extension of SWE Bench for evaluating tool-calling capabilities
**Tip:** Specifically designed for agent evaluation; more realistic than code-only benchmarks

---

## Linting & Testing

### ESLint
**What it does:** Standard JavaScript/TypeScript linting
**Tip:** Universal baseline; pair with pre-commit hooks to catch agent mistakes early

### BiomeJS
**What it does:** Fast, unified linting alternative to ESLint
**Tip:** Faster feedback loops; better for real-time agent validation

### Playwright
**What it does:** End-to-end testing and browser automation
**Use in practice:** Validation sub-agents use this for testing workflows
**Tip:** Pairs with Playwright MCP for full automation

### Prisma
**What it does:** Type-safe ORM for database schema management
**Use case:** Schema as source-of-truth for agent code generation
**Tip:** Agents handle Prisma migrations well; reduces schema drift bugs

---

## Selection Guide

**For speed-focused solo development:** Claude Code + Alacrity + minimal skills

**For team-scale shipping:** Plan/Build/Punch It + Linear Plugin + Playwright + pre-commit validation

**For observability-heavy work:** Datadog MCP + Phoenix + structured evals on SWE Bench Atlas

**For visual debugging:** Playground Skill + Cursor (for multi-file preview)

**For parallel agent orchestration:** Broomy + Superpowers Git Plugin + validation sub-agents

---

*Last updated: March 2026 | Compiled from field interviews with production practitioners*
