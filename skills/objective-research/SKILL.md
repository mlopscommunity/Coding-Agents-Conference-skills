---
name: objective-research
description: Use when you need to research a codebase to inform implementation work — understanding call paths, data flow, schema shapes, or how existing features work — and you want facts without opinions leaking in.
---

# Objective Research via Context Separation

## Overview

A two-context technique for producing unbiased codebase research. The first context (intent context) knows what you are building and decomposes the ticket into targeted research questions. The second context (research context) receives only those questions — never the ticket — and returns compressed factual findings about how the code works today.

**Core principle:** If the research agent knows what you are building, it injects opinions into facts. Confirmation bias causes it to emphasize code paths that support the anticipated solution and downplay alternatives. Separate intent from investigation.

## When to Use

- Before starting implementation on a ticket that touches unfamiliar code
- When you need to understand how an existing feature works end-to-end
- When tracing data flow, call paths, or schema shapes across multiple files
- Any time research quality matters more than speed

## When NOT to Use

- Trivial changes where you already understand the code
- Pure greenfield work with no existing code to investigate
- Quick lookups (e.g., "what version of React is installed")

## Common Mistakes

| Mistake | Why it's wrong |
|---------|---------------|
| Giving the research agent the full ticket | It will shape findings to match the anticipated solution. You get confirmation, not truth. |
| Asking broad, open-ended research questions | "How does auth work?" produces a rambling survey. Targeted questions like "What function validates JWT expiry and what does it return on failure?" produce usable facts. |
| Mixing factual questions with design questions | "What's the best way to add caching here?" is a design opinion, not research. Research should describe what exists, not what should exist. |
| Skipping the question-generation step | Jumping straight into research without decomposing the ticket means you investigate reactively — following whatever catches your eye — instead of systematically covering what you need to know. |
| Reusing the same context for research and implementation | The implementation context has intent. If it also does the research, the same bias problem returns. Use a fresh context for investigation. |

## The Two-Context Flow

```
┌─────────────────────────────────────────────────────┐
│                 INTENT CONTEXT                       │
│                                                      │
│  Inputs:  ticket / feature description               │
│                                                      │
│  Work:    Decompose into specific, factual           │
│           research questions                         │
│                                                      │
│  Output:  Numbered list of research questions        │
│           (NO ticket context attached)               │
└──────────────────────┬──────────────────────────────┘
                       │
            questions only (ticket hidden)
                       │
                       ▼
┌─────────────────────────────────────────────────────┐
│                RESEARCH CONTEXT                      │
│                                                      │
│  Inputs:  research questions + codebase access       │
│           (NEVER the ticket or feature intent)       │
│                                                      │
│  Work:    Investigate each question by reading code  │
│           Trace call paths, find schemas, map flow   │
│                                                      │
│  Output:  Factual findings per question              │
│           Compressed truth about how the code works  │
└──────────────────────┬──────────────────────────────┘
                       │
              findings (facts only)
                       │
                       ▼
┌─────────────────────────────────────────────────────┐
│           BACK TO INTENT CONTEXT                     │
│                                                      │
│  Inputs:  original ticket + research findings        │
│                                                      │
│  Work:    Design and implement with unbiased facts   │
│                                                      │
└─────────────────────────────────────────────────────┘
```

## Step 1: Decompose the Ticket into Research Questions (Intent Context)

Read the ticket or feature description. Identify what you need to *know about the existing code* before you can implement. Write specific, targeted questions that trace code paths and describe current behavior.

### Example: Good vs Bad Research Questions

Suppose the ticket is: "Add rate limiting to the /api/upload endpoint."

**Bad questions (opinion-laden, leak intent):**

| # | Question | Problem |
|---|----------|---------|
| 1 | "What's the best middleware pattern for rate limiting?" | Asks for a design opinion, not a fact about the codebase. |
| 2 | "How should we add rate limiting to uploads?" | Directly reveals the ticket. The research agent will now advocate for a particular approach. |
| 3 | "What rate limiting libraries are popular in Express?" | External opinion research, not codebase investigation. |
| 4 | "Does the upload endpoint need rate limiting?" | Asks the agent to evaluate a design decision. |

**Good questions (factual, targeted, intent-free):**

| # | Question | Why it works |
|---|----------|-------------|
| 1 | "What middleware chain does `/api/upload` pass through before reaching its handler? List each middleware in order." | Traces the exact call path. Facts only. |
| 2 | "Is there an existing rate limiting or throttling middleware anywhere in the codebase? If so, where is it applied and how is it configured?" | Discovers prior art without suggesting it should be reused. |
| 3 | "What does the request lifecycle look like for `/api/upload` — from route registration through to the response? Include error handling paths." | Maps the full flow so you understand where anything new would fit. |
| 4 | "How are middleware errors handled in this Express app? What pattern do existing middleware use to signal failures to the error handler?" | Understands the error contract without implying what errors you will add. |
| 5 | "What configuration or environment variables exist for request limits, timeouts, or resource constraints?" | Finds existing config patterns without revealing why you need them. |

### Key properties of good research questions

- **Specific**: name the file, endpoint, function, or module you are asking about
- **Factual**: ask "what does X do" not "what should X do"
- **Traceable**: ask for call paths, data flow, return values — things the agent can verify by reading code
- **Intent-free**: a reader cannot guess what feature you are building from the questions alone

## Step 2: Execute Research in a Fresh Context (Research Context)

Open a new agent context. Provide **only** the research questions — never the ticket, feature description, or any hint of what you are building. Instruct the research agent:

> Answer each question by reading the codebase. For each answer:
> - Cite specific files and line numbers
> - Show relevant code snippets
> - Describe current behavior, not recommendations
> - If the answer is "this doesn't exist," say so and stop — do not suggest what could be built

The research agent should produce compressed, factual output. One answer per question. No editorializing.

## Step 3: Bring Findings Back to the Intent Context

Return to the context that holds the ticket. Provide the research findings. Now you can design and implement with:

- Accurate understanding of existing code paths
- Knowledge of prior art and patterns already in the codebase
- No confirmation bias about which approach "should" work

## Quick Reference

| Item | Description |
|------|------------|
| Intent context | Knows the ticket. Generates questions. Receives findings. Does implementation. |
| Research context | Knows only the questions. Reads code. Returns facts. Never sees the ticket. |
| Question format | Specific, factual, traceable, intent-free |
| Research output | File paths, line numbers, code snippets, current behavior descriptions |
| What gets hidden | The ticket, feature name, desired outcome, any design preferences |
| What gets shared | Numbered research questions (stripped of context about why you are asking) |

## Key Principles

1. **Intent contaminates investigation.** When an agent knows the goal, it unconsciously filters evidence to support that goal. This is confirmation bias, and LLMs are highly susceptible to it.
2. **Research is compressed truth.** The output should describe how the code works today — not how it could work, should work, or will work after your change.
3. **Specificity beats breadth.** Five targeted questions that trace exact code paths produce more usable findings than one broad question about "how the system works."
4. **The question list is the interface contract.** It is the only thing that crosses the context boundary. Craft it carefully — if intent leaks through the questions, the technique fails.
5. **This is a one-way mirror.** The intent context sees everything. The research context sees only questions. Never break this asymmetry.

## Attribution

Based on Dex's (HumanLayer) technique from the Coding Agents: AI Driven Dev Conference. Dex demonstrates that hiding the ticket from the research agent and using separate context windows eliminates opinion injection, producing purely factual codebase research that leads to better implementation decisions.
