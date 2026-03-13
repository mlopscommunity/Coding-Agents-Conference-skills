# Session 5: Parallel Agents, Validation, and Avoiding Burnout

## Overview

Session 5 confronted the human cost of scaling agent-driven development. The technical challenge of running multiple agents in parallel collides with a hard limit: human attention. This session explored both the tooling (Broomy, git worktrees) and the organizational patterns (documentation-first, validation sub-agents) needed to keep teams sane.

## Participants

Leo Walker, Rob Ennals, Demetrios Brinkmann, Rahul Parundekar, Tanmay Tiwari, Burhan Qaddoumi

## Key Topics

**Broomy Demo** — A tool for managing parallel agent workstreams, reducing context switching and making agent coordination visible.

**Git Worktrees** — Practical infrastructure for isolating parallel work, avoiding merge conflicts, and keeping agent branches clean and independent.

**Validation Sub-Agents** — Delegate verification work to specialist agents rather than keeping it on the human critical path. Agents checking agents.

**Documentation-First Development** — Have agents document as they go, turning overhead into artifacts that improve the next iteration and knowledge sharing.

**Burnout from Parallel Agent Management** — Real warning: managing 3+ agents in parallel creates a "machine gun attack" of pull requests, test failures, and decisions. Burnout appears in 5-6 months if not managed.

**Enterprise ROI Pressures** — Organizations want to maximize agent utilization immediately. Tension between pace and sustainability. Speed without structure kills teams.

**Teaching Agents to Manage Up** — Agents can learn to communicate status, flag blockers, and request clarification without constant human prompting.

**Getting Humans Out of the Loop** — The biggest payoff comes from removing approval gates and manual checks. Every checkpoint you can eliminate is ROI.

## Top Takeaways

- **The Parallel Agent Ceiling** — 2-3 agents per domain (frontend/backend) is the practical limit before human oversight becomes unmanageable.
- **Burnout is Organizational, Not Technical** — The tech works. The problem is human stamina. Plan for this. Pace wins over sprint.
- **Validation Compounds** — Validation sub-agents are not overhead; they're multiplication. One agent writing code + one agent validating = exponential leverage.
- **Documentation Creates Leverage** — Agents writing docs as a byproduct is cheaper than humans doing it later, and pays dividends for next sprint's onboarding.
- **Governance Beats Heroics** — Enterprise success comes from sustainable processes (auto-review, clear standards, escalation paths), not from heroes working 80-hour weeks with agents.

The session was candid about the gap between what's possible and what's sustainable.
