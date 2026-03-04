# Conference Skills for Claude Code

Actionable skills extracted from the **Coding Agents: AI Driven Dev Conference** (6h 45m, 12 speakers). Each skill encodes real techniques shared by practitioners — not theory, but what they actually do.

## What Are Skills?

Skills are markdown files that teach Claude Code specific techniques. When you invoke a skill (via `/skill-name` or by loading it into context), Claude gains structured knowledge about how to apply that technique.

## The Skills

| # | Skill | What It Teaches | Key Speaker(s) |
|---|-------|----------------|-----------------|
| 1 | [Visual Regression](skills/visual-regression/SKILL.md) | Screenshot walkthroughs during dev + AI-powered visual diff at release | Rob |
| 2 | [CRISPI Planning](skills/crispi-planning/SKILL.md) | Multi-stage planning pipeline with fresh context windows per stage | Dex (HumanLayer), Sid (Anthropic) |
| 3 | [Context Window Management](skills/context-window-management/SKILL.md) | Instruction budgets, utilization thresholds, saving state to files | Dex (HumanLayer), Harrison Chase (LangChain) |
| 4 | [Adversarial Code Review](skills/adversarial-code-review/SKILL.md) | Three-agent review (builder, critic, meta-reviewer) with confidence filtering | Sid (Anthropic), Ankit (Databricks) |
| 5 | [Hooks & Enforcement](skills/hooks-and-enforcement/SKILL.md) | Using Claude Code hooks to enforce what CLAUDE.md alone cannot | Sid (Anthropic), Josh, Milan (Semgrep) |
| 6 | [Parallel Agent Management](skills/parallel-agent-management/SKILL.md) | Worktrees, containers, sub-agent contracts for running multiple agents | Sid (Anthropic), Rob, Harrison Chase (LangChain) |
| 7 | [Objective Research](skills/objective-research/SKILL.md) | Separating intent from investigation to get unbiased codebase research | Dex (HumanLayer) |
| 8 | [Expert Persona Skills](skills/expert-persona-skills/SKILL.md) | Creating short skills that activate latent domain knowledge | Rafael, Sid (Anthropic) |
| 9 | [Voice-First Planning](skills/voice-first-planning/SKILL.md) | Using speech-to-text for richer initial specs and ideation | Josh |
| 10 | [Agent-Maintained Docs](skills/agent-maintained-docs/SKILL.md) | File headers + folder READMEs enforced by hooks for agent navigation | Rob |
| 11 | [Three-Layer Memory](skills/three-layer-memory/SKILL.md) | MCP memory + auto-memory + external editor as tiered knowledge system | Audience member |
| 12 | [Product Research](skills/product-research/SKILL.md) | Two-phase research: cheap tools for gathering, Claude for synthesis | Rob, Omeh |

## Installation

### Option 1: Copy individual skills (recommended)

Pick the skills you want and copy them to your personal skills directory:

```bash
# Copy a single skill
cp -r skills/adversarial-code-review ~/.claude/skills/

# Copy several
cp -r skills/crispi-planning skills/context-window-management skills/hooks-and-enforcement ~/.claude/skills/
```

### Option 2: Copy all skills

```bash
cp -r skills/* ~/.claude/skills/
```

### Option 3: Clone the repo and symlink

```bash
git clone <this-repo> ~/projects/conference-skills
ln -s ~/projects/conference-skills/skills/* ~/.claude/skills/
```

## Usage

Once installed, skills are available in Claude Code. You can:

1. **Invoke directly**: `/skill-name` (e.g., `/adversarial-code-review`)
2. **Let Claude find them**: Claude searches installed skills when relevant to your task
3. **Reference in CLAUDE.md**: Point your project's CLAUDE.md to specific skills

## Quick Start Recommendations

**If you're new to Claude Code skills**, start with these three:
1. **Context Window Management** — immediately applicable, prevents the most common mistake (context bloat)
2. **Hooks & Enforcement** — turns CLAUDE.md suggestions into actual enforcement
3. **CRISPI Planning** — structured approach to any non-trivial task

**If you run a team**, add:
4. **Adversarial Code Review** — automated PR review with noise reduction
5. **Parallel Agent Management** — multiply throughput with worktrees

## Conference

These skills were extracted from the **Coding Agents: AI Driven Dev Conference** hosted by Demetrios. Speakers included practitioners from Anthropic, HumanLayer, LangChain, Databricks, Pinterest, Semgrep, Kilo, and more.

Each skill's Attribution section credits the specific speaker(s) and timestamps from the conference.
