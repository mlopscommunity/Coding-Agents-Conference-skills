# Pain Points & Solutions

Real problems from production agent workflows and what practitioners actually do about them.

---

## 1. Cognitive Overload from Managing Multiple Agents

**Problem:** Tracking 4+ agents in parallel becomes cognitively impossible; realistic limit is 2-3 for focused work.

**Why it happens:** Each agent creates a mental context requiring real-time status monitoring. Switching between agent states and debugging multiple code paths simultaneously exhausts working memory.

**Solutions practitioners use:**
- **Orchestrator pattern (Justin):** Use one Opus-model orchestrating agent that delegates to cheaper sub-agents. Orchestrator maintains all context and decision logic; sub-agents handle narrow tasks.
- **Broomy tool (Rob):** Custom IDE that displays session status visually, reducing mental overhead. Customizable command buttons for common workflows.
- **Workflow discipline (Rahul):** Serialize work into discrete phases (Plan → Build → Validate). Run agents sequentially within phases, not truly in parallel.

**Best practice:** 1 orchestrator + 2-3 worker agents ≤ 3 concurrent sessions total.

---

## 2. Merge Conflicts from Parallel Agent Work

**Problem:** Two agents modify the same file simultaneously, creating merge conflicts.

**Why it happens:** Agents write code faster than humans; parallel task execution increases conflict probability. Traditional sequential workflows don't scale to agent speed.

**Solutions practitioners use:**
- **Conflict-resolution skill (Rob):** Build a dedicated skill that reads recent PRs, understands intent from commit messages/issues, and resolves both syntactic and semantic conflicts automatically.
- **File isolation:** Architect code so parallel agents modify different files. Requires upfront planning but eliminates most conflicts.
- **Merge validation sub-agent:** Use separate context window to verify conflict resolution didn't break logic.

**Best practice:** Accept conflicts as learning data. Build automation to resolve them; don't prevent parallelism.

---

## 3. Agent Gets Stuck in Local Minima (Wrong Approach)

**Problem:** Agent commits to a suboptimal implementation path and can't escape without explicit intervention.

**Why it happens:** Agents optimize locally within their context window. Bad early decisions compound; backtracking isn't native to LLM reasoning.

**Solutions practitioners use:**
- **Validation sub-agents:** Deploy a separate agent in a fresh context window to review the first agent's work. Fresh eyes catch bad patterns.
- **Pre-commit hooks:** Custom hooks that trigger alternative approaches (e.g., "try refactoring this" or "check for N+1 queries").
- **Human checkpoints:** Mark critical decision points where you manually review before proceeding.
- **Explicit backtracking:** When you notice wrong direction, kill the task and restart with clearer constraints.

**Best practice:** Build validation pipelines, not manual checkpoints. Automate the "second opinion" pattern.

---

## 4. Claude Doesn't Auto-Switch into Plan Mode

**Problem:** Claude stays in default mode; doesn't automatically enter plan mode for complex tasks.

**Why it happens:** Plan mode is an explicit modal state. Claude defaults to direct execution.

**Solutions practitioners use:**
- **Manual keystroke:** Shift+Tab in Claude Code to toggle plan mode manually. It's one keystroke; just accept it.
- **Use Cursor instead:** Cursor auto-switches into plan mode for complex tasks (mentioned as advantage).
- **Skill-level orchestration:** Wrap complex tasks in a "Brainstorming Skill" that forces planning before execution.

**Best practice:** The manual keystroke is fine. If plan mode is critical for your workflow, Cursor might be worth the switch.

---

## 5. Instruction Drift in .claude.md and Skills

**Problem:** Instructions in `.claude.md` or skill definitions drift from reality as code evolves. Agents follow stale rules.

**Why it happens:** Instructions are "source of truth" for agent behavior but aren't automatically updated when code changes. No CI check enforces consistency.

**Solutions practitioners use:**
- **Re-verification cadence (Rahul):** Audit `.claude.md` every few days. Treat it like a living document that needs active maintenance.
- **Lock down critical files:** Don't allow agents to modify `.claude.md` or skill definitions unsupervised. Human approval required.
- **Distributed documentation:** Spread instructions through the codebase (READMEs, inline comments) instead of centralizing in `.claude.md`.
- **Skills as source of truth:** Put complex behavior in skills that get code review, not in instruction text.

**Best practice:** Treat `.claude.md` as high-criticality code. Version it strictly. Review changes before merge.

---

## 6. Context Window Flooding from Too Many MCPs

**Problem:** Loading all available MCPs exhausts token budget immediately. Quality of agent reasoning drops.

**Why it happens:** Each MCP adds to context length. Tools like Drata MCP lazily port 75 endpoints, creating bloat.

**Solutions practitioners use:**
- **Selective MCP loading:** Load/unload MCPs per task. Create task-specific `.claude.md` variations (e.g., "frontend-tasks.md" loads Tailwind, "backend-tasks.md" loads Datadog).
- **Abstraction layer:** If you need Drata, don't expose all 75 endpoints. Create a wrapper that maps to 3-5 high-level functions (Leo's approach).
- **Instruction budgeting:** Keep total instruction count under 80-100 tokens. Remove low-value instructions to make room for high-context tasks.
- **MCP cardinality review:** Audit MCPs quarterly. If you added it but haven't used it in 30 days, remove it.

**Best practice:** Default to zero MCPs. Add only MCPs you use weekly. Create an abstraction layer for each.

---

## 7. Bug Explanation Gap (Seeing the Bug vs. Describing It)

**Problem:** Agent can see a bug in test output or stack trace but generates vague explanations. Difficult for humans to understand root cause.

**Why it happens:** Agents see visual/contextual clues that don't map to text. They skip the "explain what you see" step.

**Solutions practitioners use:**
- **Playground Skill (Demetrios):** Generates visual debugging output. Creates hyperspecific prompts with code snippets and test outputs. Bridges the gap between visual and textual reasoning.
- **Screenshot walkthroughs:** For UI bugs, have agents capture screenshots and narrate what they see.
- **Force textual analysis:** Add a rule: "Before proposing a fix, explain the bug in plain English with 2-3 code snippets."

**Best practice:** Use Playground Skill for ambiguous bugs. Require textual explanation before fix proposals.

---

## 8. Golden Dataset Acquisition for Evals

**Problem:** Building representative eval datasets is expensive and time-consuming. You can't evaluate if you don't have benchmarks.

**Why it happens:** Creating good eval data requires domain expertise, manual labeling, and validation.

**Solutions practitioners use:**
- **Small representative samples (Rob):** Don't build huge datasets. Use 5-20-100 samples instead. Smaller datasets are easier to validate and iterate on.
- **Production trace sampling:** Use observability tools (Phoenix, Weights & Biases) to sample real production traces. Grade them with LLM-as-judge.
- **Three eval types (Rob):**
  - *Shipping evals:* Does this code pass tests and deploy?
  - *Operational evals:* Does this code stay running without alerts?
  - *Iteration evals:* Did this improve on previous version?
- **SWE Bench Atlas:** Use existing benchmarks (124 tasks). Don't build from scratch.

**Best practice:** Start with 5 examples. Run 20 iterations on those 5. Then graduate to 100. Use production data when possible.

---

## 9. Cost of Agent Usage at Scale

**Problem:** Running Opus agents 24/7 becomes expensive. 5 parallel Opus agents cost $X per day.

**Why it happens:** Agents are intelligent but not free. Token budgets compound when running multiple agents.

**Solutions practitioners use:**
- **Find where agents get stuck:** Profile agent behavior. Identify tasks where agents fail or loop. Build preventive skills for those specific cases.
- **Model tiering:** Use cheaper models (Haiku, Sonnet) for straightforward tasks. Reserve Opus for complex reasoning.
- **Cost-aware skills:** Build skills that optimize for token efficiency. Shorter prompts, better structure.
- **Throw-away agents (Rob):** "Run 5 Opus agents on a task. Throw out the 4 wrong answers. Cost is still cheaper than a PR with actual engineers."
- **Refactoring > over-planning:** Rob's insight: "Refactoring is cheap now. You can build with dumb architecture, realize weeks later it's wrong, and port it over. Still cheaper than perfect upfront planning."

**Best practice:** Measure cost per task. If >$50, redesign the task or split it. Use cheaper models as default; upgrade only when needed.

---

## 10. Team Skill Inconsistency & Code Thrashing

**Problem:** Agents modify code in different styles. Different team members create conflicting skills. Code goes through churn.

**Why it happens:** Without standardized patterns, each agent/person improvises. No shared mental model.

**Solutions practitioners use:**
- **Commit skills to git:** Treat skills like code. Code review them. Version them. This prevents divergence.
- **Team definitions:** Align on what "a good skill" looks like. What's the template? What patterns do we use?
- **Iterate together:** When a skill is useful, make it official. Share it. Improve it as a team.
- **Leo's architecture files:** Maintain a reference architecture document that all agents follow. Not rigid, but directional.

**Best practice:** First 3 skills go through PR review. After that, they're "blessed patterns" that everyone extends from.

---

## 11. Burnout from Parallel Agent Management

**Problem:** Monitoring 2-3 agents in parallel, fixing errors, validating output feels cognitively exhausting.

**Why it happens:** Manual validation breaks the automation abstraction. You're still in the critical path.

**Solutions practitioners use:**
- **Work/rest cycles (Tanmay):** Work focused for 1.5-2 hours on agent tasks, then rest for 30-40 minutes. Prevents decision fatigue.
- **Remove humans from the loop (Rob):** If you're manually checking agent output, your validation process is broken. Build automated validation pipelines instead.
- **Broomy-style tools (Leo):** Custom orchestration tools keep you in "work mode" (reviewing strategy, making design decisions) instead of context-switching to debugging.
- **Separate learning from shipping:** Don't learn by watching agents code. Learn proactively. Use agents to ship, not to teach.

**Best practice:** If validation requires human eyes, automate it. Burnout = signal that your process has a bottleneck.

---

## 12. Context Window Degradation in Long Projects

**Problem:** As projects grow, context window quality degrades. Agents start repeating past mistakes or forgetting requirements.

**Why it happens:** Long projects accumulate file history, debate threads, and reverted code. Context becomes noisy.

**Solutions practitioners use:**
- **File-level and folder-level documentation:** Create good README.md files at each level. Agents read these instead of scrolling infinite code.
- **Break work into pieces:** Instead of "build the whole system," use "build component A, build component B, integrate." Fresh context for each piece.
- **Validation in separate context window:** Don't let the same agent build AND validate. Use a fresh agent to review.
- **Screenshot walkthroughs:** For UI-heavy work, visuals reset context better than code review.
- **Commit documentation:** Each commit should explain "why" not just "what." Makes history scannable.

**Best practice:** Assume context window resets every 50KB of code. Design projects accordingly.

---

## 13. Agent Forgets Requirements Mid-Task

**Problem:** Agent starts a large task, loses track of original requirements halfway through.

**Why it happens:** Requirements buried in commit messages or issue descriptions. Not actively kept in agent's focal context.

**Solutions practitioners use:**
- **Validation sub-agent (Rob):** Deploy a second agent with fresh context that checks "did this actually solve the original problem?"
- **Comprehensive test coverage:** Write tests that encode requirements. Agent can reference tests instead of prose.
- **Screenshot walkthroughs:** For feature work, capture screenshots of expected behavior. Agents reference visuals, not memory.
- **Requirement refresh:** Every 2 hours on a long task, have the agent re-read the original requirement.

**Best practice:** Encode requirements as tests. Tests are the source of truth, not documents.

---

## 14. Code Review Bottleneck (1 hour to 2 days Waiting)

**Problem:** PRs wait 1-2 days for human code review. Agents are 100x faster at shipping than humans are at reviewing.

**Why it happens:** Code review is a sequential bottleneck. Humans can only review one PR at a time.

**Solutions practitioners use:**
- **Automated agent reviewers:** Deploy agents to check security (hardcoded secrets, SQL injection), code quality (naming, structure), and test coverage. Pass only high-confidence PRs to humans.
- **Weekly demos instead of PR blocking:** Don't block PRs on review. Demo finished work weekly. Humans decide what to keep/refactor in batch.
- **You own the code your AI writes (Rob):** This is non-negotiable. Code review should verify "is this something we'd want?" not "is this syntactically correct?"
- **Focus humans on high-value decisions:** Humans review architecture, trade-offs, scope. Agents handle syntax, testing, refactoring.

**Best practice:** 90% of PRs should auto-pass. Code review is for decisions, not validation.

---

## Summary: The Pattern

Most pain points share a root cause: **humans trying to do things agents do better.** The solution isn't always to make agents smarter. It's to remove humans from bottlenecks:

- Don't manually validate. Build validation pipelines.
- Don't manually merge. Build merge automation.
- Don't manually review code. Build automated checkers.
- Don't manually coordinate agents. Build orchestration tools.

The teams shipping fastest aren't the ones with perfect agents. They're the ones that removed humans from critical paths and let automation do its job.

---

*Last updated: March 2026 | Patterns from production deployment across 4 sessions*
