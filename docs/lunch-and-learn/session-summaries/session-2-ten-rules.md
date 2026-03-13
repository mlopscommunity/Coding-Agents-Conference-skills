# Session 2: The 10 Rules for Working with Coding Agents

## Overview

Session 2 brought together a practical toolkit for developers navigating the coordination of multiple coding agents. This was the "rules of the road" session—distilled patterns from experienced practitioners tackling real-world challenges with AI-assisted development.

## Participants

Leo Walker, Demetrios Brinkmann, Rahul Parundekar, Addison Klinke, Justin Kellam, Burhan Qaddoumi, Tristan E.

## Key Topics

The 10 Rules covered:

1. **Parallel Agents** — Managing multiple agents working simultaneously without stepping on each other's toes
2. **Plan Mode** — The importance of having agents think before they act
3. **.claude.md** — Using context files to guide agent behavior and share knowledge across sessions
4. **Skills** — Building reusable agent capabilities to avoid reinventing the wheel
5. **Bug Fixing** — Patterns for debugging agent-generated code and handling regressions
6. **Prompting** — Craft better instructions; avoid imperatives that trigger agent thrashing
7. **Terminal Setup** — Creating safe, reproducible environments for agent execution
8. **Sub-Agents** — Delegating work to specialized agents for specific tasks
9. **Data Analytics** — Using agents for exploratory analysis and report generation
10. **Learning** — Continuous improvement through iteration and feedback loops

## Top Takeaways

- **Cognitive Load is Real** — Managing more than 2-3 agents in parallel becomes cognitively overwhelming. Plan for this limit.
- **Context Files Matter** — `.claude.md` acts as institutional memory, reducing the need to re-explain patterns and standards every session.
- **Soft Prompting Works Better** — "It is important at this point to..." yields better results than hard imperatives like "You MUST..."; agents respond better to suggestions than demands.
- **Sub-Agents are Force Multipliers** — Breaking work into specialist agents reduces complexity and increases reliability.
- **The Cost of Monitoring** — If you find yourself constantly checking what agents have done, you've got a process problem, not an agent problem.

This session was practical, actionable, and grounded in what's actually working in production environments.
