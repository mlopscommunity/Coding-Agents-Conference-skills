# Session 4: Evals, Harnesses, and Code Review

## Overview

Session 4 tackled the evaluation problem—how to measure if your agents are actually producing good code, and how to automate code review in an era where AI can generate more code than humans can manually verify. The conversation ranged from practical eval frameworks to foundational benchmarks shaping the industry.

## Participants

Leo Walker, Rob Ennals, Demetrios Brinkmann, Rahul Parundekar, Robin Dehde, Burhan Qaddoumi

## Key Topics

**Three Types of Evals:**

1. **Shipping Evals** — Does this code pass tests and meet acceptance criteria? Ship-or-no-ship gates.
2. **Operational Evals** — Is the generated code maintainable, performant, and safe for production?
3. **Iteration Evals** — Does this version improve on the last? Feedback loops for continuous refinement.

**LLM-as-Judge Pattern** — Using models themselves to evaluate code quality, readability, architectural fit, and adherence to standards. Paradoxically powerful despite limitations.

**Harness Definition** — Building test infrastructure that agents can reliably run against, creating objective feedback signals.

**Automated Code Review Transformation** — Traditional code review is becoming a bottleneck. Pattern: define standards in prose → LLMs apply them → humans spot-check exceptions.

**Refactoring is Now Cheap** — With capable agents, the economics of code quality shift. Bad architectural choices can be refactored rapidly, reducing the cost of early iteration.

**SWE Bench Atlas** — Understanding industry benchmarks (like SWE Bench) helps calibrate expectations and track progress.

## Top Takeaways

- **The Review Bottleneck** — In the age of AI code generation, humans cannot review everything. Build automated review that catches 80%, spot-check the rest.
- **Evals Beat Intuition** — It's much easier to tell if something is good than to make something good. Invest in clear eval criteria first.
- **Junior Devs + Strong Evals = Accelerated Learning** — Agents with clear feedback loops become teaching tools. Agents + junior devs + evals create a powerful learning environment.
- **Refactoring Anxiety is Gone** — The cost of refactoring is now so low that perfectionism at commit-time becomes less important than shipping iterable code.
- **Measure What Matters** — Evals work best when they're aligned with actual business impact, not just test coverage or code metrics.

The session made clear: evals aren't nice-to-have, they're the foundation of trustworthy AI-assisted development.
