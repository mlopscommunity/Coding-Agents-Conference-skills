# Coding Agents: Practitioner Knowledge Base

A living resource for MLOps practitioners using coding agents in production. This repository combines techniques and guides from the **Coding Agents Conference** (March 3, 2025) and the ongoing **Coding Agents Lunch & Learn** series, hosted by the **[MLOps Community](https://mlops.community)**.

> "I've installed these skills, no idea if they are making my agent's better. But they're not making them worse!" - @missberg

**Not theory — this is what practitioners actually do**, day-to-day, with Claude Code and other agents.

## What's Inside

**16 production-ready skills** extracted from conference talks and lunch & learn sessions, plus deep-dive guides, reproducible workflows, and quick-reference resources.

This is a **living knowledge base**: new session summaries, workflows, and insights are added regularly as the Lunch & Learn series continues.

## Quick Links

- **[Watch the Conference (Full Livestream)](https://youtube.com/live/99Kxkemj1g8)** — March 3, 2025 at Computer History Museum
- **[View Conference Agenda](https://app.mlops.community/events/coding-agents/agenda)**
- **[Full Conference Transcript](docs/coding_agents_conference_transcript.md)** — 6h 45m, 1159 paragraphs

## The Skills

All 16 installable Claude Code skills, organized by source:

| Skill | What It Teaches | Source | Key Speaker(s) |
|-------|----------------|--------|-----------------|
| [Visual Regression](skills/visual-regression/SKILL.md) | Screenshot walkthroughs during dev + AI-powered visual diff at release | Conference | Rob |
| [CRISPI Planning](skills/crispi-planning/SKILL.md) | Multi-stage planning pipeline with fresh context windows per stage | Conference | Dex (HumanLayer), Sid (Anthropic) |
| [Context Window Management](skills/context-window-management/SKILL.md) | Instruction budgets, utilization thresholds, saving state to files | Conference | Dex (HumanLayer), Harrison Chase (LangChain) |
| [Adversarial Code Review](skills/adversarial-code-review/SKILL.md) | Three-agent review (builder, critic, meta-reviewer) with confidence filtering | Conference | Sid (Anthropic), Ankit (Databricks) |
| [Hooks & Enforcement](skills/hooks-and-enforcement/SKILL.md) | Using Claude Code hooks to enforce what CLAUDE.md alone cannot | Conference | Sid (Anthropic), Josh, Milan (Semgrep) |
| [Parallel Agent Management](skills/parallel-agent-management/SKILL.md) | Worktrees, containers, sub-agent contracts for running multiple agents | Conference | Sid (Anthropic), Rob, Harrison Chase (LangChain) |
| [Objective Research](skills/objective-research/SKILL.md) | Separating intent from investigation to get unbiased codebase research | Conference | Dex (HumanLayer) |
| [Expert Persona Skills](skills/expert-persona-skills/SKILL.md) | Creating short skills that activate latent domain knowledge | Conference | Rafael, Sid (Anthropic) |
| [Voice-First Planning](skills/voice-first-planning/SKILL.md) | Using speech-to-text for richer initial specs and ideation | Conference | Josh |
| [Agent-Maintained Docs](skills/agent-maintained-docs/SKILL.md) | File headers + folder READMEs enforced by hooks for agent navigation | Conference | Rob |
| [Three-Layer Memory](skills/three-layer-memory/SKILL.md) | MCP memory + auto-memory + external editor as tiered knowledge system | Conference | Audience member |
| [Product Research](skills/product-research/SKILL.md) | Two-phase research: cheap tools for gathering, Claude for synthesis | Conference | Rob, Omeh |
| [Brainstorming Planner](skills/brainstorming-planner/SKILL.md) | Structured brainstorming with agent disagreement and decision frameworks | Lunch & Learn | Demetrios |
| [Merge Conflict Resolution](skills/merge-conflict-resolution/SKILL.md) | Systematic approach to resolving multi-branch conflicts at scale | Lunch & Learn | Rahul |
| [Documentation-First Setup](skills/documentation-first-setup/SKILL.md) | Building tight feedback loops between docs and agent behavior | Lunch & Learn | Leo |
| [Validation Runner](skills/validation-runner/SKILL.md) | Composable validation pipelines with agent-friendly error reporting | Lunch & Learn | Demetrios |

## Field Guide: Guides, Workflows & References

Beyond the 16 skills, this repo contains **practitioner guides**, **reproducible workflows**, and **quick-reference resources**. These are designed to be read (not installed) and provide context for how to apply the skills.

### Guides — Deep Dives on Patterns & Practices

Longer-form resources for understanding broader concepts:

- **[10 Rules for Practitioners](guides/10-rules-practitioners-guide.md)** — Principles learned from production deployments
- **[Prompting Patterns](guides/prompting-patterns.md)** — Techniques for crafting agent instructions
- **[Team Scaling Playbook](guides/team-scaling-playbook.md)** — How to run multiple agents across teams

### Workflows — Step-by-Step Recipes

Reproducible workflows you can adapt for your own projects:

- **[Plan → Build → Punch Pipeline](workflows/plan-build-punch-pipeline.md)** — Three-stage workflow for structured delivery
- **[Opus Orchestrator Pattern](workflows/opus-orchestrator-pattern.md)** — Multi-model orchestration strategy
- **[Parallel Agents with Broomy](workflows/parallel-agents-with-broomy.md)** — Running agents in parallel safely
- **[Playground Debugging Flow](workflows/playground-debugging-flow.md)** — How to debug agent behavior iteratively
- **[Validation Sub-Agent Pipeline](workflows/validation-sub-agent-pipeline.md)** — Composable validation architecture
- **[Automated Code Review](workflows/automated-code-review.md)** — End-to-end code review pipeline

### References — Quick Lookup

Quick-reference resources for when you need answers fast:

- **[Tools & Plugins Directory](references/tools-and-plugins-directory.md)** — Catalog of available tools and integrations
- **[Pain Points & Solutions](references/pain-points-and-solutions.md)** — Common problems and how practitioners solved them
- **[Top Questions & Answers](references/top-questions-and-answers.md)** — FAQ from the community

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
git clone https://github.com/mlopscommunity/Coding-Agents-Conference-skills.git ~/projects/agents-knowledge-base
ln -s ~/projects/agents-knowledge-base/skills/* ~/.claude/skills/
```

## Usage

Once installed, skills are available in Claude Code:

1. **Invoke directly**: `/skill-name` (e.g., `/adversarial-code-review`)
2. **Let Claude find them**: Claude searches installed skills when relevant to your task
3. **Reference in CLAUDE.md**: Point your project's CLAUDE.md to specific skills

The guides, workflows, and references don't get installed — they live in the repo and you read them as needed. You can bookmark or clone this repo to have them always handy.

## Recommended Starting Path

**For solo developers:**
1. Read **[Plan → Build → Punch Pipeline](workflows/plan-build-punch-pipeline.md)** to understand the workflow
2. Install **Context Window Management** and **Hooks & Enforcement** — prevents the most common mistakes
3. Install **CRISPI Planning** — structured approach to any non-trivial task
4. Read **[10 Rules for Practitioners](guides/10-rules-practitioners-guide.md)** to calibrate expectations

**For teams:**
1. Start with solo path above
2. Install **Adversarial Code Review** — automated PR review with noise reduction
3. Install **Parallel Agent Management** — multiply throughput with worktrees
4. Read **[Team Scaling Playbook](guides/team-scaling-playbook.md)** for team-specific patterns
5. Use **[Opus Orchestrator Pattern](workflows/opus-orchestrator-pattern.md)** for multi-model coordination

## About the Conference

**Coding Agents: The AI Driven Developer Conference** was held on **March 3, 2025** at the **Computer History Museum** in Mountain View, CA. The full-day event brought together builders, founders, and ML practitioners working on coding agents in production.

### Conference Speakers & Talks

#### Keynotes

| Speaker | Company / Role | Talk |
|---------|---------------|------|
| **Demetrios Brinkmann** | MLOps Community (Host) | Opening — The Era of Side Quests |
| **Sid Bidasaria** | Co-creator, Claude Code (Anthropic) | How I Use Claude Code — Fireside Chat |
| **Scott Breitenother** | Co-founder, Kilo Code | Scaling AI-Assisted Development — Lessons from 25 Trillion Tokens |
| **Harrison Chase** | Founder, LangChain | The Agent Harness — Building General Purpose Agents |
| **Sam Partee** | CTO, Arcade.dev | General Purpose Agents — Auth, Identity & Tool Use |
| **Dexter Horthy** | Founder, HumanLayer | The CRISPI Planning Pipeline — Structured Agent Workflows |
| **Jess Wang** | BrainTrust | Evals for AI Tooling — Quantifying Ship Decisions |
| **Ankit Mathur** | Databricks | Mosaic Coding Agent — Enterprise AI Development at Scale |
| **Zach Lloyd** | Founder & CEO, Warp | Agent Orchestration — The Year of Multi-Agent Workflows |

#### Lightning Talks

| Speaker | Company / Role | Talk |
|---------|---------------|------|
| **Faye Zhang** | Staff AI Engineer & Tech Lead, Pinterest | Productionizing Sub-Agents for LLM Post-Training |
| **Yannis He** | Co-founder, SWE-bench Pro (Scale AI) | The Next Generation of Coding Agent Benchmarks |
| **Erin Ahmed** | Head of Product, Cleric | Building a Learning Agent — Stateful AI SRE |
| **Milan Williams** | Senior Product Manager, Semgrep | Three Security Tips for Coding Agents |
| **Ash Lewis** | CEO, Fastino Labs | Choosing & Maintaining the Right Model for Agents |

#### Workshops

| Workshop | Instructor |
|----------|-----------|
| 5 Prompts to Ship Production Code 2x Faster With AI | Mihail Eric |
| Optimizing Codebases for Agents | Shrivu Shankar |
| Software Libraries with No Code | Drew Breunig |

#### Unconference / Audience Sessions

The afternoon featured open unconference sessions where attendees shared techniques live. Contributors whose insights made it into these skills include: **Rob**, **Josh**, **Rafael**, **Chad**, **Yari**, **Omeh**, **Niels**, and others.

## Lunch & Learn Series

An ongoing series of 90-minute deep dives on specific agent patterns and techniques. Hosted by **Demetrios Brinkmann**, **Rahul Parundekar**, and **Leo Walker** from the MLOps Community.

Session transcripts and summaries are available in [`docs/lunch-and-learn/`](docs/lunch-and-learn/). New sessions are added regularly — this is a living resource.

Current sessions included in this knowledge base:
- Brainstorming with agents
- Merge conflict resolution at scale
- Documentation-first development patterns
- Validation and testing pipelines

## Attribution

Each skill's `SKILL.md` file includes an **Attribution** section that credits the specific speaker(s), session, and timestamps where the technique was shared.

The full conference transcript is available at [`docs/coding_agents_conference_transcript.md`](docs/coding_agents_conference_transcript.md) (6h 45m, 1159 paragraphs).

## Next Events

**AI Agents Summit — Seattle** — April 17th
We're organizing the next agent-focused conference. Early bird tickets available at https://luma.com/ai-agents-summit-seattle

Keep an eye on [mlops.community/events](https://mlops.community/events) for upcoming Lunch & Learn sessions.

## About MLOps Community

The [MLOps Community](https://mlops.community) is a global network of ML practitioners, engineers, and data scientists. We focus on the practical side of machine learning operations, AI systems, and agent-driven development.

- **Website**: https://mlops.community
- **Community**: https://community.mlops.community (Slack, discussions, events)
- **Events**: Conferences, lunch & learns, and virtual meetups year-round

This knowledge base is maintained by the community. Contributions, corrections, and new insights are welcome.
