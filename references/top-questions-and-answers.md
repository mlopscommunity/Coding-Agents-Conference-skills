# Top Questions & Answers

Real questions from teams adopting coding agents, with answers from practitioners running 2-3 concurrent agents in production.

---

## Q1: How Many Agents Can You Realistically Run in Parallel?

**Short answer:** 2-3 for focused coding. 6-8 technically possible but cognitively unsustainable. Orchestrator pattern scales better.

**Long answer:**

Every practitioner we interviewed agreed: **2-3 agents max for direct parallel work.** Beyond that, you lose the ability to track context, debug failures, and make mid-course corrections.

Why 2-3?
- **Cognitive load:** Each agent is a mental context. Switching between 4+ agents exhausts working memory.
- **Debugging complexity:** When 3 agents fail simultaneously, which one do you fix first? Who depends on whom?
- **Output validation:** You can review 2-3 code outputs and catch issues. 8 outputs require automated validation (which you should build anyway).

**The exception: Orchestrator pattern (Justin's approach)**

Run 1 Opus orchestrator agent that delegates to 2-3 cheaper sub-agents. Orchestrator maintains all state and decision logic. Sub-agents handle narrow, well-defined tasks. Result: scales to 6-8 total agents without cognitive overload because you only manage 1 (the orchestrator).

**Real cost comparison:**
- 3 Opus agents = cognitive overload, token budget ~$15/day
- 1 Opus orchestrator + 2-3 Haiku workers = light management, token budget ~$3/day, better output

**Recommendation:** If you're new to agents, start with 1. Graduate to 2 when you have clear task separation. Only scale to 3+ with explicit orchestration.

---

## Q2: When Should Something Be a Prompt vs. a Rule vs. a Skill?

**Short answer:** Context-dependent. No one-size-fits-all. Think about persistence and reusability.

**Long answer:**

Leo's framework: "It's like deciding what language or framework to use — no one-size-fits-all, but patterns emerge."

**Prompt (for one-off requests):**
- Use when: You're solving a specific, non-repeating problem
- Example: "Analyze this PR for security issues"
- Lifespan: Single task
- Overhead: Minimal

**Rule (in .claude.md or conditional files):**
- Use when: Standard behavior that applies across many tasks
- Example: "Always use const, not let" or "Format all error messages as: [ERROR_CODE] Description"
- Lifespan: Persistent; applies to all agent work
- Overhead: Must maintain and version; easy to drift
- Caution: Keep `.claude.md` short. Use it for critical standards only, not tutorials.

**Skill (reusable workflow):**
- Use when: Complex multi-step workflow you'll repeat 5+ times
- Example: "Plan a feature" or "Find and fix N+1 queries" or "Validate code against architecture"
- Lifespan: Long-term; evolves over time
- Overhead: Requires code review; must maintain
- Benefit: Encapsulates complexity; prevents knowledge loss

**Decision tree:**
```
One-time task? → Prompt
Every agent task? → Rule
Repeating workflow? → Skill
Complex, evolving process? → Skill
```

**Caution:** Don't put tutorials in rules. Use progressive disclosure. Store detailed context in skills or reference files, load conditionally.

**Team pattern (Rahul):**
- Year 1: Few centralized skills
- Year 2: Skills in different domains (frontend-skills, backend-skills)
- Year 3: Each domain has 10-20 battle-tested skills
Result: Agents ship faster because they inherit team knowledge.

---

## Q3: How Do You Keep Agents from Going Off the Rails?

**Short answer:** Validation sub-agents in separate context. Pre-commit hooks. Rules. Screenshot walkthroughs. Don't micromanage steps.

**Long answer:**

"Off the rails" means: agent commits to a weird implementation, breaks tests, forgets requirements, or takes a 30-minute detour instead of asking for clarification.

**Prevention strategies:**

**1. Validation sub-agent (most effective)**
- Deploy a second agent in a fresh context window to review the first agent's work
- Fresh eyes catch what the original agent misses
- Cost: 20% overhead; value: prevents 80% of mistakes
- Example: Agent A builds a feature. Agent B reads the original requirement and checks if feature actually solves it.

**2. Pre-commit hooks**
- Custom scripts that trigger alternative approaches: "If this code touches database schema, run DB migration review"
- Catch categories of mistakes before they land in main branch
- Low overhead; high ROI

**3. Rules and constraints**
- Don't try to control every decision (micromanagement)
- Instead, set hard boundaries: "Never modify schema without migrations" or "All new endpoints require tests"
- Let agent make choices within constraints

**4. Screenshot walkthroughs**
- For UI bugs, have agents capture before/after screenshots and narrate what they see
- Forces explicit description; prevents hand-waving
- Use Playground Skill for hyperspecific prompts

**5. Requirement refresh (for long tasks)**
- Every 2 hours on a large task, have agent re-read the original requirement
- Prevents drift
- One-line addition to task prompt

**What doesn't work:**
- Micromanaging steps (too expensive)
- Trusting first output (too optimistic)
- Multiple validators (too expensive; one sub-agent is enough)

**Best practice:** Assume 1 in 10 agent outputs is wrong. Design validation into the pipeline, not as manual inspection.

---

## Q4: Should I Use Claude Code Terminal or an IDE?

**Short answer:** Personal preference. No wrong choice.

**Long answer:**

**Claude Code (Terminal)**
- Who uses it: Justin, Rahul (primary workflow)
- Advantages: Raw speed, less UI overhead, scriptable
- Pairing: Justin adds custom scripts in Alacrity for branch info and token usage tracking
- Best for: Developers comfortable with CLI, teams doing heavy scripting, token-conscious workflows
- Gotcha: No visual preview while agent works; you're checking output post-execution

**IDE (Cursor, VS Code + Copilot)**
- Advantages: Visual file preview, multitasking (you can work while agent runs), visual debugging
- Best for: Developers who like visual feedback, UI-heavy work, pair programming
- Gotcha: Slightly slower; more UI overhead
- Special: Cursor auto-switches to plan mode (unlike Claude Code's manual shift+tab)

**Hybrid approach (Burhan):**
Use IDE while agents work on non-blocking tasks. Switch to terminal for focused, linear work. Best of both worlds.

**Rahul's recommendation:**
"Use Claude Code as your terminal." It's not a replacement for IDEs; it's a new terminal paradigm.

**Decision framework:**
- If you like looking at code while things run: IDE
- If you like speed and automation: Terminal (Claude Code)
- If you're learning agent workflows: Start with terminal; easier to understand what's happening
- If you're shipping production: Whatever your team aligns on

---

## Q5: How Big Should .claude.md Be?

**Short answer:** Keep it short. Use skills for detailed context.

**Long answer:**

`.claude.md` should be a **constitution**, not a tutorial.

**Size guidelines:**
- **Too small:** <200 words (not enough guidance)
- **Goldilocks:** 300-800 words (clear standards without bloat)
- **Too big:** >2000 words (agent skims it; context bloat)

**What goes in .claude.md:**
- Critical architectural patterns (3-5 max)
- Non-negotiable coding standards (const vs let, error format, naming conventions)
- Security constraints (no hardcoded secrets, SQL injection prevention)
- Links to detailed context (e.g., "See architecture.md for service boundaries")

**What goes elsewhere:**
- Tutorials: Skills or README.md
- Decision histories: Git commit messages
- API documentation: Inline code comments or separate docs/
- Example implementations: Links to example PRs

**Progression (Rahul's pattern):**
- Year 1: ".claude.md tells you everything"
- Year 2: ".claude.md points to skills; skills are the source of truth"
- Year 3: "Developer unfolds .claude.md once on day 1. Rarely reads it again."

**The DRY principle applies:** Don't repeat instructions in .claude.md if they exist in code comments or skills.

**Version control:** Treat .claude.md like high-criticality code. Require approvals. Don't let agents modify it unsupervised.

---

## Q6: How Do You Evaluate If Coding Agents Are Actually Helping?

**Short answer:** Three types of evals (shipping, operational, iteration). Use LLM-as-judge. Track reopened tickets. Use small samples (5-100).

**Long answer:**

Most teams measure agents on shipping speed alone. That's incomplete.

**Three eval types (Rob's framework):**

**1. Shipping evals:** Does the code pass tests and deploy?
- Metric: % of agent-generated PRs that merge without changes
- Target: 60-80% (hitting 100% means tasks are too easy)
- Tools: Your CI/CD pipeline; it's already measuring this

**2. Operational evals:** Does the code stay running without alerts?
- Metric: Agent-generated code bug rate vs human code bug rate (in production)
- Timeframe: Track for 2-4 weeks post-deployment
- Tools: Datadog MCP or your observability platform
- Example: "Agents generated 3 bugs per 100K lines; humans generated 2. Close enough."

**3. Iteration evals:** Did this agent task improve on the previous version?
- Metric: Defect reduction, performance improvement, code quality (e.g., LOC reduced, complexity down)
- Timeframe: Measure before/after on the same task
- Example: "First agent pass wrote 500 LOC. After feedback loop, second pass wrote 350 LOC with same functionality."

**Golden dataset acquisition (don't overdo it):**
- Start with 5 representative tasks. Iterate 20 times.
- Graduate to 20 tasks after 5 cycles.
- Full benchmark (100+) only for final validation.
- Use SWE Bench Atlas (124 pre-made tasks) instead of building from scratch.
- Sample production traces from your observability tool; grade them with LLM-as-judge.

**Simple metrics to track:**
- Code review time: (was 2 days, now 30 minutes)
- Time to ship: (was 5 hours, now 1.5 hours)
- Reopened tickets: (agent code had 2 reopens, human code had 3; neutral)
- Context switches: (are you thinking about code or managing agents?)

**Caution:** Don't wait for perfect data. 70% certainty on a decision is good enough. Ship evals incrementally.

---

## Q7: What About Code Review with AI-Generated Code?

**Short answer:** Automated agent reviewers first (security, quality). Humans for exceptions. Weekly demos instead of blocking PRs. You own all code your AI writes.

**Long answer:**

This is the hardest cultural shift. Humans evolved reviewing human-written code. AI code is different.

**Review strategy (3-tier system):**

**Tier 1: Automated (agent reviewers)**
- Scan for security: hardcoded secrets, SQL injection, missing sanitization
- Scan for code quality: naming conventions, test coverage, cyclomatic complexity
- Pass/fail: Obvious mistakes
- Cost: ~1 Haiku call per PR
- Goal: Eliminate 90% of obvious mistakes before human review

**Tier 2: Human judgment (focused)**
- Does this PR make architectural sense?
- Does this solve the right problem?
- Would I want this in production?
- Humans skip syntax/style (agent reviewers handled it); focus on judgment calls
- Cost: 10 minutes per PR vs 1 hour (old way)

**Tier 3: Operational (in production)**
- Deploy and monitor. If agent code breaks, hotfix immediately and add a pre-commit rule to prevent recurrence.
- This is normal. Iterate.

**Weekly demos instead of PR blocking:**
- Don't gate shipping on code review
- Demo finished work weekly to stakeholders
- Stakeholders decide what to keep, refactor, or discard in batch
- Move code quality conversations from async (PR comments) to sync (demos)

**You own the code your AI writes (non-negotiable):**
- Agents don't understand intent like humans do
- Your job is to verify intent is met, not to validate syntax
- You're responsible for bugs, security, performance
- This mindset prevents blame-shifting ("the agent did it")

**Rob's wisdom:**
"Your job is not to build the product. Your job is to build the team that builds the product. If you're personally reviewing every line of agent code, you've failed at that job."

---

## Q8: How Do You Handle Merge Conflicts with Parallel Agents?

**Short answer:** Agents are good at this. Build a skill that reads recent PRs, understands intent, and resolves conflicts. Less coordination needed upfront.

**Long answer:**

Merge conflicts are **features**, not bugs. They're signals that agents are working in parallel.

**Approach (Rob's pattern):**

**1. Accept conflicts as learning data**
- Don't try to prevent all conflicts (requires serializing all work)
- Instead, build tooling to resolve them automatically

**2. Conflict-resolution skill**
- Input: Two conflicting versions of a file + recent PRs/commits explaining intent
- Process: Agent reads both versions, understands what each agent was trying to do, merges semantically (not just syntactically)
- Output: Merged version that preserves both intents
- Example: Agent A adds error handling to a function. Agent B refactors the same function. Skill merges both changes.

**3. Merge validation**
- Deploy a separate agent in a fresh context to verify the merged code still passes tests
- Catches false merges

**Why this works:**
- Agents understand code intent (what the change was trying to achieve)
- Humans see conflicts as text diffs (lots of cognitive work)
- Agents are faster and more reliable at semantic merging

**Less coordination needed upfront:**
- Old way: "Agent A, you work on auth. Agent B, you work on API. Don't touch each other's files."
- New way: "Agent A and Agent B, both work on whatever. We'll resolve conflicts after."
- Result: Faster shipping, better parallelism

**Best practice:** Build this skill once. Reuse across all projects.

---

## Q9: Is Extensive Upfront Architecture Still Necessary?

**Short answer:** Less so. You can refactor cheaply now. But some architecture discipline still helps.

**Long answer:**

This question reveals a big shift in how teams think about code.

**Rob's take (radical):**
"Refactoring is cheap now. You can do totally dumb architecture, realize weeks later it's wrong, port over and it's fine. Agents make refactoring so fast that you don't have to be perfect upfront."

- Example: You designed a monolithic database schema. Weeks later, you realize you need sharding. Old way: major rewrite. New way: agent refactors schema + writes migrations + updates all queries. Cost: maybe 4 hours of agent time.
- Implication: You can ship faster with "good enough" architecture and iterate.

**Leo's take (moderate):**
"I still keep architecture files for pattern consistency. Not rigid, but directional. Agents follow patterns better than they generate patterns."

- Architecture docs aren't about upfront design; they're about consistency
- Agents can reference existing patterns instead of inventing new ones
- Prevents the "every service uses a different pattern" problem

**Practical reality:**
- If you have 0 architecture: chaos. Agents produce 10 different solutions to the same problem.
- If you have rigid architecture: waste. Agents follow rules even when they're now suboptimal.
- If you have pattern libraries: sweet spot. Agents reference patterns, improvise when appropriate.

**What changed:**
- Upfront architecture was about risk mitigation (rewrite later is expensive)
- Now rewrite is cheap
- So architecture is about consistency and knowledge sharing, not risk mitigation

**Recommendation:**
- Don't spend 3 months on architecture upfront
- Spend 1 week documenting patterns and assumptions
- Ship
- Refactor at week 6 if you need to
- Agents handle the refactoring

---

## Q10: How Do You Prevent Burnout from Managing Agents?

**Short answer:** Work/rest cycles. Get humans out of the loop. Use orchestration tools. Build validation pipelines, not manual checkpoints.

**Long answer:**

Agent fatigue is real. You're managing complexity that humans didn't evolve to manage.

**Strategy 1: Structured work/rest cycles (Tanmay)**
- Work focused for 1.5-2 hours on agent tasks
- Rest for 30-40 minutes
- Prevents decision fatigue
- Prevents the "check the agent just one more time" spiral (which leads to phone-scrolling, not rest)

**Strategy 2: Remove humans from the loop (Rob)**
- If you're manually checking agent output, your validation process is broken
- Build automated validation pipelines instead
- Example: Agent writes code → automated tests pass? → auto-merge OR flag for review
- Example: Agent finds bugs → automated test verifies the fix → auto-deployed

Humans should only be in the loop for judgment calls, not validation.

**Strategy 3: Broomy-style tools (Leo)**
- Custom orchestration tools that display agent status visually
- Reduces context switching
- Keeps you in "work mode" (making decisions) instead of "debugging mode" (fixing agent mistakes)
- Result: more productive, less cognitively taxing

**Strategy 4: Separate learning from shipping**
- Don't learn by watching agents code
- Learn proactively: read articles, experiment in separate projects, pair program with humans
- Use agents to ship, not to teach
- This prevents the "I must understand every line" anxiety

**What causes burnout:**
- Manual validation (you're still in critical path)
- Unclear ownership (who's responsible if this breaks?)
- Unclear success criteria (how do I know this is done?)
- Cognitive overload (managing 5+ agents)

**What prevents burnout:**
- Automated validation (you're not in critical path)
- Clear ownership (this agent owns this component)
- Clear success criteria (tests pass = done)
- Orchestration tools (1 agent to manage, not 5)

**Red flag:** If you're working >4 focused hours on agents per day, something's wrong. Either you're micromanaging, or your agents are flaky.

---

## Q11: What About Junior Developer Learning?

**Short answer:** Learning and shipping are different problems. Separate them. AI accelerates learning. Build a mentoring mechanism outside the shipping pipeline.

**Long answer:**

This is trickier than people assume. Agents are great for shipping; they're not great for teaching.

**The problem:**
- Juniors watch agents generate code and learn passively (not great)
- Juniors are blocked on simple tasks because agents are doing them (creates dependency)
- Juniors don't build mental models (they need to struggle a bit)

**Separate mechanisms:**

**For learning:**
- Pair program with experienced developers
- Read code reviews (see why decisions were made)
- Own small, scoped features end-to-end
- Use Perplexity/Claude for answering questions (Leo does this; learns faster than traditional mentorship)
- Journal about decisions and trade-offs

**For shipping:**
- Juniors own features with agent assistance, not agent-driven
- Junior writes code; agent refactors/optimizes
- Junior makes decisions; agent implements
- Gradually shift to agent-driven as junior gains skill

**The accelerated learning path:**
- Leo's observation: "I've learned more from Perplexity and Claude than from previous mentors."
- Why: Questions answered immediately. Multiple explanations available. Can dive deep on topics that matter to current work.
- Implication: Juniors should use AI heavily for learning; just not as a replacement for mentorship

**What juniors should NOT do:**
- Delegate all work to agents (you learn nothing)
- Trust agent code without review (misses why it was written that way)
- Skip the architectural thinking (agents do that for you)

**What juniors SHOULD do:**
- Use agents to accelerate learning on non-critical work
- Own features end-to-end with human feedback
- Ask agents to explain code (teaches reasoning)
- Build one component alone, then optimize with agent's help

**Team responsibility:**
- Pair juniors with senior code reviewers (not agents)
- Give juniors "steering wheel" tasks where they make decisions
- Use agents for "passenger seat" tasks where they observe

---

## Q12: How Do You Handle Costs?

**Short answer:** Find where agents get stuck. Build preventive skills. Use cheaper models. Throw-away agents are cheaper than engineers.

**Long answer:**

Token costs become real at scale. 5 Opus agents cost ~$25/day. That's real money.

**Cost optimization strategies:**

**1. Find bottlenecks (profiling)**
- Which tasks do agents loop on most?
- Which tasks timeout and get retried?
- Which tasks consume 10x more tokens than expected?
- Use observability tools to track token spend per task type
- Target the top 3 money-wasters

**2. Build preventive skills**
- Once you identify a bottleneck, build a skill that prevents it
- Example: "Agents get stuck finding N+1 queries" → build a skill that auto-detects them
- Cost: 2 hours to build skill. Saves 50 hours of token waste per month.

**3. Model tiering**
- Haiku for simple tasks (formatting, summarization, basic refactoring)
- Sonnet for mid-complexity (feature implementation, debugging)
- Opus for complex reasoning (architecture decisions, novel problems)
- Cost reduction: 5-10x by matching model to task

**4. Token budgeting**
- Set monthly token budget per agent
- When agents hit budget, they switch to cheaper model or get paused
- Forces teams to optimize

**5. Throw-away agents (Rob's insight)**
- Run 5 Opus agents on a hard problem
- Take the best 2 answers
- Throw out the other 3
- Total cost: Still cheaper than 1 engineer PR with back-and-forth
- Implication: Don't optimize for efficiency. Optimize for speed, then cut costs later.

**Cost comparison:**
- Traditional engineer: $150-250K/year = $580-960/day
- 5 Opus agents on a task: ~$5 total
- 20 task failures on Opus, 15 succeed: $5 for 15 successful solutions
- That's $0.33 per solution

**When to use cheap vs expensive models:**
- Cheap (Haiku): "Format this code" or "Find all TODO comments"
- Expensive (Opus): "Design a caching strategy" or "Refactor this architecture"

**The reframe:**
Stop thinking "how do I make agents cheaper?" Start thinking "where do agents add the most value?" Build skills around those bottlenecks. Everything else can use cheaper models.

---

## Quick Decision Matrix

| Question | Decision |
|----------|----------|
| Starting with agents? | 1 agent, Claude Code terminal |
| Ready to parallelize? | 1 Opus orchestrator + 2 Haiku workers |
| Lots of context? | Cut .claude.md. Move to skills. |
| Code breaking? | Build validation sub-agent. |
| Review bottleneck? | Deploy automated agent reviewer. |
| Costs high? | Profile where agents loop. Build preventive skill. |
| Burnout? | Remove humans from loops. Automate validation. |
| Junior learning? | Separate learning path from shipping. |

---

## The Meta-Pattern

Most of these answers come back to one insight: **automate the bottlenecks, don't control the agents.**

Teams getting stuck:
- Micromanage agents ("check this step")
- Validate manually ("I'll review the output")
- Coordinate tightly ("Agent A, you do auth")
- Optimize for perfection ("make the code perfect")

Teams shipping:
- Build pipelines (automated validation)
- Remove humans from loops (pre-commit hooks)
- Parallelize freely (let agents conflict, then merge)
- Optimize for speed (refactor later)

The shift from "how do I make agents obey?" to "how do I remove myself from the critical path?" is the biggest mindset change in agent adoption.

---

*Last updated: March 2026 | Q&A synthesized from interviews with teams shipping 50-500 PRs/month with agent assistance*
