# The 10 Rules — A Practitioner's Guide to Working with AI Coding Agents

## Introduction

These 10 rules didn't come from a whiteboard exercise or research paper. They emerged from real practitioners in the trenches — developers, MLOps engineers, and architects who've built production systems with AI coding agents. This guide captures their battle-tested insights from Session 2 of the Coding Agents Lunch & Learn series.

These aren't dogma. They're patterns that work, mistakes that cost time, and breakthroughs that shipped real code. Use them as a starting point, adapt them to your workflow, and contribute back what you learn.

---

## Rule 1: Work with Multiple Agents in Parallel

**The Rule:** Don't try to do everything with one agent. Spawn multiple agents for independent tasks.

**What This Means:**
You can run several agents simultaneously on different components or phases of a project. One agent researches API specs while another implements the frontend. A third writes tests. They work in parallel, compress your timeline, and let you leverage multiple perspectives.

**The Practitioner Reality:**

The cognitive load of managing agents is real. Rahul's principle: "I cannot have brain cycles enough for more than three." While data shows some teams run 6-8 agents in parallel, most practitioners effectively manage 2-3 at once. Beyond that, tracking state, context, and progress becomes overhead rather than acceleration.

**The Breakthrough Approach:**

Justin Kellam's breakthrough: **Don't manage multiple agents yourself—let an Opus agent do it.** He created one orchestrating Opus agent that managed sub-agents internally, coordinating work across different features. Result: 5 PRs shipped across different codebases, pulled together and validated by the orchestrator. Single cognitive load for maximum parallel work.

Addison Klinke expanded this: Mix coding tasks with non-coding work. While agents A and B code features, have agent C do PR reviews, update design docs, or manage project tracking. Better CPU utilization, less context switching.

**Cursor's Angle:**
Cursor can spin off multiple agents to solve the same problem independently, then judge which performs best. It's like having a small panel of experts and taking the strongest answer.

**Practical Tips:**
- Start with 2-3 agents. Add more only if you have an orchestrating agent managing them
- Parallelize different features, not the same feature (unless you're explicitly comparing approaches)
- Use agents for different task types: one for code, one for docs, one for research
- Designate one agent as orchestrator if you're running more than 3

**Gotchas:**
- More agents ≠ faster shipping. Context-switching and coordination overhead can kill speed
- Sub-agents need clear scope boundaries or they'll interfere with each other's work
- You still need to verify outputs—parallel agents still produce mistakes

---

## Rule 2: Start Complex Tasks in Plan Mode

**The Rule:** Before execution, spend time in planning mode. Clarify the problem, break it into steps, identify what can parallelize.

**What This Means:**
Plan mode is where you think hard. You ask clarifying questions, challenge assumptions, map out the execution strategy, and identify which parts can run in parallel versus sequentially. Only then do you move into execution.

**The Practitioner Reality:**

Burhan Qaddoumi: "I spend MOST of my time in plan mode, not execution." The engineers who shipped fastest weren't the ones who jumped straight to coding. They were the ones who spent serious time thinking first.

Demetrios created a Brainstorming Skill that transformed this. By asking rigorously follow-up questions and forcing clarity before execution, plan quality skyrocketed. The questions matter more than the plan document itself.

**Claude vs. Cursor Behavior:**

Important limitation: Claude doesn't automatically shift INTO plan mode. It can exit plan mode, but it won't enter it without being told. Cursor, however, can choose to switch into plan mode proactively. If you're using Claude Code, you need to explicitly request plan mode or use a planning skill.

**Parallel Orchestration:**

Use planning to identify which sub-tasks can run in parallel. Include notes on task dependencies: "Agent A and Agent B can run in parallel during this phase, then Agent C waits for both and integrates." This becomes your execution blueprint.

**Practical Tips:**
- Create a planning skill that asks: "What are the dependencies? What can parallelize? What's the highest-risk assumption?"
- Write the plan in structured markdown, not prose
- Identify which agents will execute which phases
- Call out assumptions that need validation early
- Include time estimates so you know when to check in on parallel work

**Gotchas:**
- Over-planning kills momentum. Give yourself a time box (e.g., 15 minutes of planning per hour of execution)
- Plans change once execution starts. Build in feedback loops to update the plan
- Don't plan so far ahead that context becomes stale

---

## Rule 3: Invest in Claude Markdown Rules (.claude.md)

**The Rule:** Write organization-wide rules and coding standards in `.claude.md` files. Treat them like living documentation that agents reference.

**What This Means:**
`.claude.md` files are markdown files that live in your repo and tell AI agents how you work, what your standards are, and what they should know about your codebase. They're like codified practitioner knowledge—conventions, naming patterns, testing requirements, error-handling philosophy.

**The Reality of Rule Management:**

Boris's approach (via Leo): After EVERY correction an agent makes, update your `.claude.md`. If an agent misunderstood your style or violated a convention, that's a signal. Document it so the next agent doesn't make the same mistake. This is iterative learning baked into your workflow.

Token budget is realistic: 76 tokens for org-wide rules, 4K tokens for project-specific context. You have room to be specific.

**The Centralization vs. Distribution Debate:**

There's tension: should you keep all rules in one place for coherence, or spread them throughout the codebase for context-locality?

Addison Klinke's answer: Spread documentation throughout the codebase instead of centralizing. Keep critical rules in `.claude.md`, but embed specific guidance where it matters—comments in the code, READMEs in folders, docstrings in files. Progressive disclosure: agents see broad rules first, then find specific context as they navigate code.

Cursor's solution: Conditional rule loading. Load specific rules only when agents work with certain parts of the codebase ("load this rule when working with front-end UI"). This keeps context lightweight and relevant.

**The Instruction Drift Risk:**

Rahul warns: if agents themselves can edit your `.claude.md`, you risk instruction drift. Rules get subtly modified, assumptions bake in, and suddenly you've drifted from your original standards. Protect these files—human review before merge.

**Practical Tips:**
- Start with 3-5 core rules: code style, testing requirements, error handling, naming conventions
- Update after every agent correction that reveals a gap
- Keep it concise—each rule should be 2-3 sentences max
- Reference specific files or patterns: "All API handlers go in `/src/handlers/`"
- Use conditional rules if your project has distinct domains (frontend, backend, infra)

**What to Include:**
- Code style and linting rules
- Testing requirements (unit, integration, coverage %)
- Error handling conventions
- Naming patterns (camelCase, snake_case, prefixes)
- Architectural constraints (monolith vs. micro)
- Security non-negotiables
- Approval processes for sensitive code

**Gotchas:**
- Don't let rules get too prescriptive. Agents need room to problem-solve
- Rules without context are ignored. Explain the WHY
- Stale rules are worse than no rules. Archive rules that no longer apply

---

## Rule 4: Create Custom Skills and Commit to Git

**The Rule:** Build reusable skills (markdown files + optional resources) for recurring patterns. Treat them like code—version, share, iterate.

**What This Means:**
A skill is a prompt pattern or workflow you've documented. It might be "how to debug frontend issues," "how to refactor a module," or "how to write a design doc." You write it in markdown, optionally include templates or examples, and commit it to git. Your team uses it, improves it, and checks back in the updated version.

**Skills as Multipliers:**

Claude Ception: An ambitious idea—after every task, have an agent evaluate "can I learn a skill from this?" and automatically create new skills. Over time, you build a library of repeatable patterns your team can reference.

**Real Skills in Production:**

- **Playground Skill** (Demetrios): Visual debugging. Map the architecture, click around the app, generate hyperspecific bug-fixing prompts that you copy back to Claude. Pairs agent work with human visual feedback.

- **Planet → Build → Punch It** (Rahul): A three-skill workflow for feature development. Planet = planning (parse Linear ticket, identify dependencies). Build = implementation (end-to-end feature development). Punch It = testing and fixing (iterate until tests pass and issues resolve).

- **Create Skill** (Rahul): His first skill in any new project. When starting something new, an agent uses Create Skill to map out what other skills you'll need and where documentation gaps are.

- **Organizational Skills for PMs**: Create tickets, search GitHub repos, find bugs. Democratize agent use—non-engineers can leverage agents for project management tasks.

**Practical Tips:**
- Start with one skill per major workflow (development, debugging, docs, deployment)
- Write skills like you're teaching a junior engineer: explicit, step-by-step, with examples
- Include edge cases and gotchas
- Version your skills—when you improve one, increment the version
- Review and refine skills as a team. They're not static.
- Commit skills to git so they're reviewed and tracked like code

**Skill Structure:**
```
skill-name/
├── SKILL.md          # The prompt/workflow
├── template.md       # Optional: template for agent to fill
├── examples/         # Optional: real examples from production
│   ├── example1.md
│   └── example2.md
└── README.md         # Optional: when/how to use this skill
```

**Gotchas:**
- Skills can become stale. Review them quarterly, update them as patterns evolve
- Don't create a skill for everything. If it's a one-off, it's not a skill yet
- Skills need clear inputs and outputs or agents will misuse them
- Over-documenting skills kills usage. Keep them concise

---

## Rule 5: Fix Bugs By Itself

**The Rule:** Create systems where agents can identify, reproduce, and fix bugs without constant human intervention.

**What This Means:**
Instead of handing an agent a bug report, set up workflows where the agent can access logs, run tests, inspect the system, and iterate toward a fix. The agent becomes capable of independent debugging.

**Three-Skill Bug System:**

Rahul's workflow:
1. **Planet**: Parse the bug report from Linear. Understand what's broken, expected vs. actual behavior, reproduction steps.
2. **Build**: Implement the fix end-to-end. Code changes, test updates, anything needed to resolve it.
3. **Punch It**: Run the full test suite. Verify the fix. Find any regressions. Iterate until green.

This splits the cognitive load and makes each phase focused and testable.

**Visual Debugging with Playground Skill:**

Demetrios' Playground Skill: Many bugs are visual or contextual. The agent can't see them in logs. Solution: map the architecture visually, click around the app, observe behavior, then generate a hyperspecific bug-fixing prompt based on what you observed together. You take a screenshot, point to the issue, the agent generates the fix prompt. Copy it back to Claude Code and iterate.

**Model Selection Matters:**

- **Sonnet for quick debugging**: Fast iteration, good for "try this fix, run tests, repeat" cycles. Cheaper, faster feedback loop.
- **Opus for complex bugs**: Subtle issues, architectural problems, distributed system debugging. You need the reasoning power.

**Sub-agent Specialization:**

Different agents for different domains:
- Frontend debugger: skilled with browser tools, visual bugs, CSS, JavaScript
- Backend debugger: logs, database state, API contracts
- Infrastructure debugger: deployment logs, infrastructure-as-code, networking

**Pre-commit Hooks:**

Add value by enforcing tests before merge. Agents run tests locally, catch issues before they ship, iterate faster.

**Practical Tips:**
- Make logs accessible and structured. Agents debug better with good observability
- Keep tests fast. Slow test suites kill iteration speed
- Document reproduction steps in tickets—agents need to know how to trigger the issue
- Use feature flags to deploy fixes safely and roll back if needed
- Track which bugs took longest and extract patterns—those become skills

**Gotchas:**
- Agents can get stuck in fix loops, thrashing without progress. Set iteration limits and escalate
- Production bugs are different from dev bugs. Real-time monitoring and fast rollback are critical
- Not all bugs are fixable by agents. Scope carefully—some need human context

---

## Rule 6: Level Up Your Prompting

**The Rule:** As context windows grew and models improved, the way you prompt agents fundamentally changed. Shift from aggressive directives to collaborative language.

**What This Means:**
Stop thinking of prompting as "how do I force the agent to do this?" and start thinking of it as "how do I work with the agent effectively?" The language, structure, and tone matter more than you'd expect.

**The Gentler Language Shift:**

Rahul's key insight: **"It is important at this point to..." works MUCH better than "You MUST..."**

Why? Aggressive directives trigger overcorrection and thrashing. Agents become defensive, double-check themselves excessively, and paradoxically make more mistakes. Gentler language—collaborative, suggestive—lets agents reason clearly and execute confidently. You're training a coworker, not commanding a robot.

**Evolution of Context and Prompting:**

The evolution is real: 8K → 32K → 64K → 200K → millions of tokens. As context grew, prompting evolved. You don't need the aggressive, hyper-explicit prompts from 2023. Modern models can handle nuance, can infer intent, and actually reason better without constant constraints.

**Code Documentation Matters:**

- Docstrings at file level help agents understand the module's purpose
- Function-level docstrings explain intent, not just parameters
- Inline comments for non-obvious logic
- Good variable names reduce the need for explanation

Agents understand code significantly better when documentation is present. It's like pairing with an engineer who reads the code first.

**Prompting Has Changed:**

The prompting landscape 2 years ago: wild, explicit, "you MUST NOT make this mistake, you MUST consider this, you MUST check..."

Today: Much less crazy prompting needed. Modern models are stable enough that clear, collaborative language works. You're no longer fighting the model's instability.

**Training a Coworker Model:**

- **Explicit at first**: New project? Detailed prompts, context, examples
- **Less over time**: As agents understand your patterns, shorter prompts work
- **Periodic level-sets**: Every few weeks, refresh context and recalibrate

It's exactly like onboarding a junior engineer. Heavy guidance upfront, less as they learn.

**Anthropic's Prompt Engineering Resources:**

Anthropic is the only provider with official, rigorous prompt improvement resources. Use them. They're battle-tested across production systems.

**Practical Tips:**
- Use collaborative language: "Consider...", "It might help to...", "You might want to think about..."
- Front-load context: spend effort on the setup, less on directives
- Let agents ask clarifying questions if they're stuck
- Use examples. Show the output you want, not just describe it
- Refine prompts iteratively. If an agent misunderstands, that's signal about clarity
- Document your reasoning in prompts, not just requirements

**What Not To Do:**
- Don't over-constrain with "MUST" directives
- Don't assume agents need hand-holding on basics
- Don't change prompts mid-conversation without recapping context
- Don't use acronyms without defining them

**Gotchas:**
- Collaborative language can feel less direct. It's not. It's more effective
- Long preambles don't help. Concise, clear context beats walls of text
- Context freshness matters. Stale context leads to stale responses

---

## Rule 7: Terminal and Environment Setup

**The Rule:** Choose your tools based on what you need to do while agents work.

**What This Means:**
You'll spend hours with agents running. Where you do that work—terminal, IDE, browser—affects productivity. Pick based on your workflow, not convention.

**The Tool Preferences:**

- **Leo prefers IDE** for preview and visual features. Seeing what agents produce in real-time, visual debugging, design-system exploration.

- **Justin Kellam**: Alacrity terminal with custom scripts. His terminal shows branch info, token usage, agent status. When agents cook, he knows what's happening without asking.

- **Rahul**: Claude Code itself as terminal for git commands. Why switch contexts? Agents can handle git, pull latest, check status. Keep everything in one place.

- **Burhan**: VS Code for multitasking. While agents run long tasks, he's in VS Code handling other work—reviewing PRs, exploring code, sketching next steps.

**The Principle:**

Do you need to do other things while agents cook? If yes, IDE with good multitasking support. If no, terminal or agent terminal is fine. If you're doing visual work (design, debugging), preview capability matters.

**Practical Tips:**
- Set up your terminal or IDE for visibility: branch, token usage, agent status
- Keyboard shortcuts for switching between agent contexts and your work
- Have a way to quickly review agent outputs without leaving your environment
- Use split-screen if your monitor allows (terminal + IDE, terminal + browser preview)
- Customize your environment as you learn what you actually use

**Gotchas:**
- Switching contexts constantly kills focus. Pick an environment and stick with it for a session
- Token tracking in your terminal is useful—agents will use hundreds or thousands of tokens per task
- If agents can run terminal commands, make sure your shell is safe and logged

---

## Rule 8: Keep Main Agent Context Clean with Sub-agents

**The Rule:** Don't overload one agent with everything. Route distinct problems to sub-agents, keep the main agent's focus sharp.

**What This Means:**
Your main orchestrating agent stays uncluttered. When a sub-task emerges—"read and summarize all these files," "generate a design doc," "find every reference to this function"—spin up a sub-agent for it. The sub-agent focuses, reports back, main agent integrates.

**Why This Works:**

Context bloat is real. A 200K context window can hold a lot, but agents reason better with focused, relevant context. If you dump everything—codebase, requirements, design docs, logs, examples, constraints—even if it fits, the agent has to sift through noise. Sub-agents let you parallelize and keep each agent's context tight.

**Real-World Scale:**

- **Rahul**: Explicitly asks Claude to create sub-agents for parallel tasks. "Create 3 sub-agents to refactor these modules in parallel."
- **Burhan**: Opus spawned 80+ sub-agents to read and summarize all files in a codebase. The main agent never had to hold 80 files in context. Each sub-agent read 1-2 files, summarized, moved on. Main agent integrated the summaries.
- **Justin Kellam**: His Git plugin (Superpowers Git) automatically knows when to use sub-agents. "Create sub-agent for this." It suggests parallelizable tasks.

**Teams of Agents:**

Claude 4.6 can create "teams of agents" with Opus 4.6. This is orchestration built in. You define roles—planner, coder, reviewer—and Opus coordinates them. They work together, escalate to you when needed, parallelize where possible.

**Sub-agent Handoff:**

Clear handoff is critical:
- **Input**: What is this sub-agent responsible for?
- **Output**: What does it return to the main agent?
- **Scope**: Where does its authority end?

Bad handoff: "Go figure out the codebase." Good handoff: "Read files A, B, C. Extract the data flow between them. Return a 2-paragraph summary and list of files you examined."

**Practical Tips:**
- Create sub-agents for: research, summarization, file reading, specific domain work (frontend, backend)
- Give sub-agents clear mandates. Scope is your friend
- Have sub-agents report back in structured format (JSON, markdown table, bullet points)
- Main agent reviews and integrates sub-agent outputs
- Keep main agent's context for synthesis, decision-making, integration

**Gotchas:**
- Sub-agents increase complexity. Use them when parallelization or focus gains are clear
- Sub-agents need to know who they're reporting to and where their output goes
- If sub-agents create their own sub-agents, you can lose track. Set depth limits
- Sub-agent outputs might be incomplete or wrong. Main agent still needs to validate

---

## Rule 9: Cloud for Data Analytics

**The Rule:** For static HTML, visualizations, and data analysis, cloud environments (notebooks, dashboards, Python-generated PNGs) are powerful force multipliers.

**What This Means:**
Some problems are best solved in a Jupyter notebook or interactive dashboard. Agents can generate code, you run it in the cloud, see results, iterate. Great for analytics, metrics analysis, profiling, trend detection.

**Real Use Cases:**

- **Burhan**: Averages, moving averages, trends, month-to-month analytics. Generate notebooks that compute metrics. Visualize them. Share dashboards with stakeholders.
- **Tristan E**: Datadog MCP for metrics analysis. Agents query Datadog, pull profiling data, generate dashboards. Real production metrics feeding into agent analysis.
- **Notebooks and Dashboards**: From code analysis, agents can produce notebooks (Jupyter, Colab) that explore codebase patterns, generate reports.

**Why It Works:**

Text-based debugging has limits. Once you need to see data, visualize trends, or compute aggregate stats, notebooks shine. Agents generate the code, you run it, visual feedback informs next steps. It's collaborative.

**Practical Tips:**
- Use Jupyter for exploratory work: agents code, you iterate
- Use dashboards for ongoing metrics: set and forget, check daily
- Export results as PNGs or static HTML for reports
- Keep notebooks in git for reproducibility
- Document assumptions in notebook markdown

**Gotchas:**
- Notebooks can become messy. Agents should write clean, documented code
- Dashboards need maintenance. Metrics change, queries break
- Not everything benefits from visualization. Use for metrics/analytics, not general coding
- Real-time dashboards need infrastructure. Static exports are safer

---

## Rule 10: Learning with Claude

**The Rule:** The original promise of LLMs: interactive learning. Use agents as teaching partners.

**What This Means:**
LLMs were built for dialogue. They're teaching partners who explain concepts, show examples, debug your understanding, and adapt to your knowledge level. Use this for learning new frameworks, languages, architectural patterns, or domains.

**The Accelerated Learning Curve:**

Leo: "I've probably learned more about code from Perplexity and Claude than from previous mentors."

Why? Because:
- Agents answer immediately. No waiting for senior engineer's calendar
- They explain at your level. Confused? They adjust
- They show examples, run code, iterate
- They work at your pace, not a team standup's pace
- Conversation is private and judgment-free

**Real Learning Scenarios:**

- New language or framework: "I'm learning Rust. Here's a problem. Explain the right approach."
- Architecture patterns: "I don't understand CQRS. Show me a real example, then help me implement it."
- Debugging understanding: "I think the issue is X. Am I right? If not, what am I missing?"
- Code review learning: Agents review code, explain issues, suggest patterns

**The Feedback Loop:**

Learning works best with feedback. Agents give immediate feedback on your code, your understanding, your approach. You iterate based on that feedback. Loop tightens learning.

**Practical Tips:**
- Use agents for just-in-time learning. Learn what you need when you need it
- Ask for explanations, not just solutions. "Explain why this is the right approach"
- Show agents your code and ask for critique. Learn from correction
- Work through examples together. Concept + implementation + feedback
- Take notes. Learning goes deeper when you externalize it

**Gotchas:**
- Agents can explain things confidently and incorrectly. Cross-reference with docs
- Learning is slower than copy-paste answers. That's by design. Slow is better
- You still need human mentors. Agents are complements, not replacements
- Learning conversations can wander. Keep focus: what's the learning goal?

---

## Synthesis: Working as a Practitioner

These 10 rules form a system:

1. **Parallelize work** (Rule 1) based on a solid **plan** (Rule 2)
2. **Document your standards** in `.claude.md` (Rule 3) and create **reusable skills** (Rule 4)
3. **Debug systematically** (Rule 5) using **good prompting** (Rule 6)
4. **Set up your environment** (Rule 7) and **keep focus with sub-agents** (Rule 8)
5. **Use the right tool** for analytics (Rule 9)
6. **Learn continuously** (Rule 10)

They're not sequential steps. They're patterns that reinforce each other. Follow the rules that fit your workflow, skip the ones that don't, and build your own practices from there.

The goal is simple: Work faster, ship better, learn deeper.

---

## Contributing & Iteration

Have you applied these rules? Found something that works better? Update this guide. These rules live and evolve with the community. Document your patterns, share your breakthroughs, and help the next practitioner ship faster.

**This guide is version 1.0.** Your feedback makes version 1.1.
