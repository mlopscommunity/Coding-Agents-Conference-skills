---
name: brainstorming-planner
description: Use when starting a complex project, task, or feature to deeply clarify requirements, identify scope boundaries, map dependencies, and structure work into phases before any coding begins.
---

# Brainstorming Planner

## Overview

The Brainstorming Planner skill dramatically improves plan mode by forcing rigorous clarification before execution. Rather than jumping straight into coding, this skill intercepts the planning phase and asks detailed follow-up questions to uncover ambiguities, identify assumptions, and structure the work effectively.

**Core principle:** Investment in upfront planning saves 10x the time in rework. Spending 20-30 minutes on clear requirements prevents 2-3 hours of implementation backtracking.

**Dependency:** Claude Code CLI with standard claude command.

## When to Use

- Starting a complex task or feature implementation
- When requirements are stated but specifics are unclear
- Before work involving multiple files or interdependent systems
- Before cross-team handoffs or parallel work
- When you sense ambiguity but can't quite articulate it

## When NOT to Use

- Trivial tasks (single-line fixes, obvious changes)
- When requirements are already crystal clear and fully scoped
- Emergency fixes where speed matters more than planning

## Common Mistakes

| Mistake | Why it's wrong |
|---------|---------------|
| Skipping ahead to coding | You'll discover missing requirements mid-implementation and waste time pivoting. Start here. |
| Not getting explicit confirmation | You've analyzed the problem, but are you and the user aligned? Confirm before coding. |
| Treating vague answers as "good enough" | "I don't know" is valuable data—it's an assumption to validate before you build on it. |
| Not documenting assumptions | Untested assumptions are the #1 source of rework. Write them down, mark them as "untested." |
| Forgetting about edge cases | Edge cases are how implementations break. Identify them early. |
| Skipping risk identification | Risks identified upfront change how you approach implementation. Risks discovered mid-project derail everything. |

## The Planning Process

### Step 1: Clarify the Goal

Ask the user to describe their goal in their own words. Then reflect back what you heard:
- What problem are they solving?
- Who benefits from this?
- How will success be measured?

### Step 2: Identify Scope Boundaries

Probe for scope creep:
- What is explicitly IN scope?
- What is explicitly OUT of scope?
- What looks like it might be in scope but isn't?
- Are there any "nice-to-have" features that could be deferred?

### Step 3: Map Dependencies and Assumptions

Ask about:
- What existing code/systems does this depend on?
- Are there APIs, databases, or external services involved?
- What assumptions are you making about how things work?
- Have any of those assumptions been validated?

### Step 4: Identify Edge Cases

Push for thoughtful edge case coverage:
- What happens if [common error scenario]?
- What about users with [unusual configuration]?
- How should [boundary condition] be handled?
- Are there performance or scalability concerns?

### Step 5: Define Acceptance Criteria

Get explicit:
- What does "done" look like?
- How will this be tested?
- What metrics or behaviors confirm success?
- Are there specific edge cases that MUST be handled?

### Step 6: Break Into Phases

Structure the work:
- What's the minimal viable version?
- What can be parallelized?
- What has dependencies on other phases?
- In what order should phases be executed?
- Estimate effort for each phase (rough: hours/days)

### Step 7: Identify Risks and Unknowns

Ask:
- What could go wrong?
- What parts are you least confident about?
- Are there any integration points you need to understand better?
- Should we spike/research anything before starting?

### Step 8: Get Explicit Confirmation

Before moving forward:
- "Does this capture what you're trying to do?"
- "Are you happy with the scope and phasing?"
- "Should we validate any assumptions before starting?"

## Output Format

Provide a structured summary:

```
## Brainstorming Results

### Goal
[Clear statement of what we're solving]

### Scope
- In scope: [list]
- Out of scope: [list]

### Key Assumptions
- [assumption 1] - Status: [validated/untested]
- [assumption 2] - Status: [validated/untested]

### Dependencies
- [system/file/service]: [how it's used]

### Edge Cases
- [case 1]: [how it's handled]
- [case 2]: [how it's handled]

### Acceptance Criteria
- [ ] [criterion 1]
- [ ] [criterion 2]

### Proposed Phases
1. [Phase 1 name] (~[effort estimate])
   - Subtask 1
   - Subtask 2
2. [Phase 2 name] (~[effort estimate])
   - etc.

### Risks & Unknowns
- [risk/unknown]: [mitigation or investigation needed]

### Next Steps
Ready to proceed: [ ] YES [ ] NO
If no, what needs clarification?
```

## Tips

- Don't accept vague answers. Keep asking until you understand.
- If the user says "I don't know," treat that as valuable information—it's an assumption to validate.
- Write down all assumptions. Untested assumptions are the biggest source of rework.
- The time spent here saves 10x more time later.
- If the user is vague about what "done" looks like, that's a red flag. Push back hard.
- "Nice-to-have" features frequently sneak into scope. Call them out explicitly.

## Configuration Notes

### Project-Specific Customization

1. **Add your team's acceptance criteria standards**: If your team has a definition of "done," reference it here.

2. **Reference key dependencies**: Update with common systems in your codebase:
   ```
   Common dependencies in this project:
   - Database schema in `/sql/schema.sql`
   - API contracts in `/api/openapi.yaml`
   - Configuration in `config.yaml`
   ```

3. **Add domain-specific edge cases**: Customize with realistic edge cases from your domain:
   ```
   For ML ops projects, consider:
   - What happens if training data is empty or malformed?
   - How are model versions tracked?
   - What's the rollback procedure?
   ```

4. **Adjust phase breakdown criteria**: If your team has standard phases (design → implementation → testing → deployment), specify them.

## How to Invoke

In a Claude Code session:

```
/brainstorming-planner

[Describe your task]
```

Or ask directly:
```
I need to [task description]. Let's brainstorm this first.
```

## Key Principles

1. **Upfront clarity prevents rework.** Spending 20-30 minutes on brainstorming prevents 2-3 hours of implementation backtracking.
2. **Document all assumptions.** Untested assumptions are the biggest source of mid-project pivots.
3. **Scope creep kills projects.** Explicitly call out what's NOT in scope.
4. **Edge cases matter.** Identify them early so they shape implementation strategy.
5. **Risk identification changes approach.** Risks discovered upfront are managed. Risks discovered mid-project derail everything.

## Attribution

Based on techniques from the Coding Agents Lunch & Learn Series. Demetrios Brinkmann contributed the core principle and practitioner insight: "It has made my plan mode so much better. It basically clarifies the shit out of your plan mode."
