# Prompting Patterns for Coding Agents

A practical guide to effective prompting strategies for coding agents, distilled from real-world usage patterns in production systems.

## The Evolution of Agent Prompting

Two years ago, working with coding agents required extensive, complex prompting with elaborate tag systems and careful management of system vs. user roles. Today, model improvements have dramatically reduced this burden. The best practices documented here reflect the current state: simpler, more natural prompting that lets models do their job with minimal overhead.

## 1. Gentle Guidance Over Harsh Commands

**The Pattern:** Use soft guidance language instead of absolute directives.

Instead of:
```
You MUST follow this step exactly. Do not deviate.
```

Use:
```
It is important at this point to ensure we handle this step carefully.
```

**Why it works:** Harsh commands cause agents to overcorrect and thrash. They interpret mandatory language as permission to overthink and second-guess themselves, often getting stuck in loops of validation and re-validation. Gentle guidance provides the same direction while preserving the agent's flexibility to problem-solve.

**Practical impact:** This is particularly effective for sensitive operations like database migrations, authentication flows, or multi-step refactorings where there's structured guidance but room for intelligent adaptation.

## 2. Progressive Disclosure in Skills and Rules

**The Pattern:** Don't front-load your entire context. Let agents discover what they need.

**Implementation strategies:**

- **Skill descriptions:** Keep `.claude.md` skill summaries brief (1-2 sentences). Expand details only when the agent opens the file. Long preambles flood the context window immediately.

- **Conditional rule loading:** Tools like Cursor support loading rules conditionally. Example: "Load this rule when working with front-end UI" or "Apply these patterns for database operations."

- **Scenario-specific documentation:** Instead of centralizing all rules, reference specific files for specific scenarios: "For authentication-related tasks, open `auth-patterns.md`" or "For schema changes, consult `database-guidelines.md`"

- **Folder structure as navigation:** A well-organized file hierarchy with clear README.md files at each level helps agents navigate through progressive disclosure naturally.

**Why it works:** Agents have limited context windows. Progressive disclosure ensures they load only relevant information when needed, leaving room for actual work.

## 3. Documentation as Context

**The Pattern:** Treat documentation as a primary control mechanism for agent behavior.

**What to document:**

- **File-level comments:** Every file should have a header explaining:
  - What the file does
  - How it fits into the system
  - Key design decisions and why they were made
  - How it relates to other files

- **Function-level docstrings:** Help agents navigate and understand expected inputs/outputs without reading implementation.

- **Folder-level README.md:** Include:
  - Purpose of the folder
  - Philosophy and design patterns used
  - What each file is for
  - Dependencies between files

**The core insight:** Agent time is cheaper than human time. Make agents maintain the documentation as part of their workflow. This creates a compounding benefit: better documentation means agents navigate more effectively next time.

**Practical approach:** Rather than centralizing documentation, spread substantial documentation throughout the codebase. This lets agents discover context where they're already working, reducing context-switching costs.

## 4. Psychological Prompting

**The Pattern:** Trigger specific thinking patterns through role and context framing.

Examples that work:
- "Think like a senior FAANG engineer designing for scale" (not just "engineer")
- "Apply O(log N) thinking to this problem"
- "How would you design this for a distributed system?"
- "Reuse existing patterns from the codebase"

**Show, don't tell:** Provide examples of the thinking pattern you want:
```
Here's how we solve similar problems in codebase X - apply this approach.
```

**Why it works:** Triggering the right mental model is often more effective than fine-tuning individual instructions. A senior engineer mental model activates different heuristics than a generic "engineer" role.

## 5. Scope and Identity Framing

**The Pattern:** Help agents understand their role and context in the larger system.

**What to establish:**
- Who the agent is (their role/expertise area)
- Where they are (project, subsystem, team context)
- Which models to use for which tasks (document this in `.claude.md`)
- What their constraints are (performance, security, compatibility)

**Memory as context reduction:** Well-managed memory reduces the need for repetitive explanations in subsequent interactions. If the agent remembers previous context about your standards and architecture, you don't need to re-explain on every task.

## 6. Iterative Refinement Mindset

**The Pattern:** Treat prompting like training a new coworker.

**Progression:**
1. **Early phase:** Explicit, detailed instructions
2. **Growth phase:** Gradually require less instruction as agent learns your patterns
3. **Mature phase:** High-level direction with agent autonomy

**Critical practice:** Periodically level-set on expectations. Don't optimize every prompt iteration — this becomes time-consuming with diminishing returns. Instead:
- Run with a prompt version for 2-3 tasks
- Observe patterns
- Make targeted adjustments
- Run another 2-3 tasks

This approach captures the important improvements without analysis paralysis.

## 7. Anti-Patterns to Avoid

**Over-specifying with mandatory language**
- "You must follow this exactly" → agents overcorrect and get stuck
- Use gentle guidance instead

**Front-loading massive context**
- Dumping entire architectural documentation upfront → context window floods immediately
- Distribute documentation throughout codebase instead

**Letting agents update `.claude.md` unsupervised**
- Instruction drift happens naturally over time
- Keep `.claude.md` as human-curated source of truth

**Micromanaging tool usage and code details**
- "Use this specific pattern for this part" repeated at scale → doesn't scale and wastes context
- Trust agents with implementation given good architecture docs

**Loading too many MCPs at once**
- Agents get confused about which tools to use when options proliferate
- Load tools progressively or segment them by context

## 8. Model Selection as Prompting Strategy

**The Core Insight:** Model choice is part of your prompting strategy, not separate from it.

**Practical allocations:**

- **Sonnet:** Quick iteration, debugging, tight back-and-forth loops. Good for exploration and rapid feedback.

- **Opus:** Complex planning, orchestration, multi-agent coordination. Good for systems-level decisions and long-horizon tasks.

- **Opus with extended thinking:** Planning phases where deep reasoning is valuable. Then hand off to simpler models for execution.

**Cost optimization:** Rather than "use the cheapest model," think about this: "5 Opus agents at $5 each, throw out 4, still cheaper than a PR with actual engineers reviewing and fixing the output."

**When to use each:**
- Planning → Opus (extended thinking when beneficial)
- Execution → Sonnet (faster, cheaper, sufficient capability)
- Review/validation → Opus (catches subtle issues)
- Iteration/feedback → Sonnet (tight loop cost matters)

## Key Takeaways

1. Gentle guidance works better than harsh mandates
2. Let agents discover context progressively, don't front-load
3. Documentation is a control mechanism — use it strategically
4. Trigger thinking patterns through framing and examples
5. Keep prompts simple and let model improvements do the work
6. Iterate on prompts like you'd train a coworker, not obsessively optimize
7. Model selection is a prompting strategy
8. Remember: model capabilities improve continuously, so design prompts assuming tomorrow's models are cheaper and more capable
