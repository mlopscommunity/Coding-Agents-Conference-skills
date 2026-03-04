---
name: three-layer-memory
description: Use when setting up persistent memory for Claude agents across tools and projects, or when deciding where a piece of knowledge should be stored so the agent can recall it later.
---

# Three-Layer Memory Architecture

## Overview

A tiered memory system that gives Claude agents persistent knowledge across sessions by storing different types of information in the right place. Layer 1 (Memory MCP) holds cross-application global memory shared between Claude Desktop and Claude Code. Layer 2 (auto-memory) holds per-repository project context that travels with the codebase. Layer 3 (external markdown editor) serves as a research library for long-form artifacts the agent can reference but does not own.

**Core principle:** Different types of knowledge belong in different memory tiers. Putting everything in one place creates noise; splitting it correctly means the agent always has the right context without being overwhelmed.

**Dependency:** Layer 1 requires the Memory MCP server. Layer 3 requires Joplin, Obsidian, or any markdown-based knowledge tool accessible via file path or MCP.

## When to Use

- When starting a new project and configuring how the agent should remember things
- When you notice the agent forgetting decisions, preferences, or context between sessions
- When you work across multiple tools (Claude Desktop + Claude Code) and need shared state
- When you have research artifacts (design docs, API references, vendor comparisons) that the agent should consult

## When NOT to Use

- Single-session throwaway tasks where persistence has no value
- Projects where you are the only consumer of the context (just use your own notes)
- As a replacement for proper documentation -- memory tiers supplement docs, they do not replace them

## Common Mistakes

| Mistake | Why it's wrong |
|---------|---------------|
| Storing everything in CLAUDE.md | CLAUDE.md is for *instructions*, not knowledge. It tells the agent how to behave, not what it knows. Dumping facts there makes it bloated and slow to parse. |
| Putting project-specific decisions in global Memory MCP | Global memory pollutes other projects. A database schema decision for Project A is noise when working on Project B. Use Layer 2 per-repo auto-memory instead. |
| Skipping CLAUDE.md routing instructions | Without explicit instructions telling the agent which tier to use, it will default to whatever is easiest -- usually forgetting entirely. The routing config is what makes the system work. |
| Using Layer 3 for things that change frequently | The external research library is for stable reference material. If the content changes every sprint, it belongs in Layer 2 auto-memory where it is versioned with the repo. |
| Treating memory as write-only | Memory that is never pruned becomes stale and misleading. Review and clean each layer periodically. Old decisions that have been reversed are worse than no memory at all. |

## The Three Layers

### Layer 1: Memory MCP (Global Cross-Application Memory)

Memory MCP provides persistent storage that is shared across Claude Desktop and Claude Code. This is for knowledge that applies regardless of which project or tool you are working in.

**What belongs here:**
- Personal preferences (coding style, communication tone, review standards)
- Tool configurations and credentials references
- Cross-project architectural principles you always follow
- Team conventions that apply to every repository

**Setup:**

Configure the Memory MCP server in your Claude configuration so it is available in both Claude Desktop and Claude Code.

```json
{
  "mcpServers": {
    "memory": {
      "command": "npx",
      "args": ["-y", "@anthropic/memory-mcp"]
    }
  }
}
```

**Example stored memories:**
- "Always use conventional commits with scope prefixes"
- "Prefer composition over inheritance in TypeScript projects"
- "When reviewing PRs, check for missing error boundaries first"

### Layer 2: Claude Code Auto-Memory (Per-Repository Context)

Claude Code maintains a `.claude/memory/` directory inside each repository. This is auto-managed memory that the agent reads at the start of every session. It is versioned with the repo and scoped to that project only.

**What belongs here:**
- Project architecture decisions and their rationale
- Dependency choices and why alternatives were rejected
- Known gotchas, workarounds, and tech debt notes
- Sprint-level context (current priorities, blocked items)
- Team member roles and ownership areas for that project

**Directory structure:**

```
your-repo/
  .claude/
    memory/
      MEMORY.md          # Auto-managed by Claude Code
    CLAUDE.md            # Project-level agent instructions
```

**Example MEMORY.md content:**

```markdown
# Memory

## Architecture
- API uses Express with Zod validation middleware
- Database is PostgreSQL with Drizzle ORM (chose over Prisma for edge runtime support)
- Auth is handled by Clerk -- do not build custom auth

## Current State
- Migration to React Server Components is in progress (app/ directory)
- Legacy pages/ directory is frozen -- no new routes there
- Rate limiting is not yet implemented on public endpoints

## Known Issues
- The test suite leaks database connections if tests fail mid-transaction
- Safari has a z-index bug on the modal component -- workaround in components/Modal.tsx
```

### Layer 3: External Markdown Editor (Research Library)

Use Joplin, Obsidian, or any markdown-based tool as a structured research library. This layer holds long-form reference material that is too large or too stable for auto-memory, but that the agent should be able to consult when needed.

**What belongs here:**
- API documentation summaries for key integrations
- Vendor comparison notes and evaluation criteria
- Design documents and RFC archives
- Interview notes, user research findings
- Conference notes and technique references

**Access methods:**
- Point Claude at the file path directly: `Read the research notes at ~/notes/research/`
- Use an Obsidian or Joplin MCP server for search-based retrieval
- Reference specific files from CLAUDE.md instructions

**Example Obsidian vault structure:**

```
~/notes/
  research/
    apis/
      stripe-webhook-patterns.md
      openai-token-counting.md
    architecture/
      event-sourcing-tradeoffs.md
      edge-runtime-limitations.md
    vendors/
      auth-provider-comparison.md
      hosting-platform-evaluation.md
```

## Configuring CLAUDE.md to Route the Agent

This is the critical step. Without explicit routing instructions in your CLAUDE.md, the agent will not know which tier to use. Add a section like this to your project-level `.claude/CLAUDE.md`:

```markdown
# Memory Tiers

## When storing or retrieving knowledge, use the correct tier:

### Global (Memory MCP)
- Personal coding preferences and standards
- Cross-project conventions
- Tool configurations
- Use: `memory_store` and `memory_retrieve` MCP tools

### Project (Auto-Memory)
- Architecture decisions for THIS repo
- Current project state and priorities
- Known issues and workarounds specific to this codebase
- Update: Edit files in `.claude/memory/` directly

### Research (External Library)
- Long-form reference docs, API guides, comparison notes
- Path: `~/notes/research/`
- Read-only from agent perspective -- I maintain this library
- Consult when you need background on a technology or vendor decision
```

## Step-by-Step Setup

### Step 1: Set up Layer 1 (Memory MCP)

Install and configure the Memory MCP server in your global Claude configuration (`~/.claude.json` or Claude Desktop config). Verify it works by asking Claude to store and retrieve a test memory.

### Step 2: Set up Layer 2 (Auto-Memory)

In each repository, ensure `.claude/memory/MEMORY.md` exists. Seed it with current architecture decisions and project state. Claude Code will update this automatically as it learns about the project.

### Step 3: Set up Layer 3 (Research Library)

Create a structured markdown vault in Joplin or Obsidian. Organize by topic, not by date. Keep files focused -- one concept per file. If using an MCP server for the editor, configure it alongside Memory MCP.

### Step 4: Add routing instructions to CLAUDE.md

Add the routing configuration (shown above) to your project-level `.claude/CLAUDE.md`. This tells the agent exactly when to use each tier. Without this, the three layers exist but the agent will not use them correctly.

### Step 5: Test the full loop

Ask the agent a question that requires each tier:
- "What is my preferred commit style?" (should check Layer 1)
- "What ORM does this project use?" (should check Layer 2)
- "What were the tradeoffs we found when evaluating auth providers?" (should check Layer 3)

Verify the agent routes to the correct tier for each.

## Quick Reference

| Item | Location | Scope |
|------|----------|-------|
| Memory MCP config | `~/.claude.json` or Claude Desktop config | Global, all projects and tools |
| Auto-memory | `.claude/memory/MEMORY.md` per repo | Single project, versioned with code |
| Research library | `~/notes/research/` (Joplin/Obsidian vault) | Cross-project, manually maintained |
| Routing instructions | `.claude/CLAUDE.md` per project | Tells agent which tier to use when |
| Global agent instructions | `~/.claude/CLAUDE.md` | Personal defaults across all projects |

## Key Principles

1. **Instructions and knowledge are different things.** CLAUDE.md holds instructions (how to behave). Memory tiers hold knowledge (what the agent knows). Do not mix them.
2. **Scope determines tier.** If it applies everywhere, Layer 1. If it applies to this repo, Layer 2. If it is reference material, Layer 3.
3. **The routing config is the glue.** Without explicit instructions in CLAUDE.md telling the agent which tier to consult, the three layers are just files the agent ignores.
4. **Prune regularly.** Stale memory is worse than no memory. Review each tier monthly. Remove decisions that have been reversed, projects that are archived, and research that is outdated.
5. **Layer 3 is read-only for the agent.** You maintain the research library. The agent consults it. This prevents the agent from polluting curated reference material with generated summaries.

## Attribution

Based on a technique shared by an audience member during the Q&A session at the Coding Agents: AI Driven Dev Conference. The three-layer pattern emerged from their experience managing memory across Claude Desktop and Claude Code for multiple active projects.
