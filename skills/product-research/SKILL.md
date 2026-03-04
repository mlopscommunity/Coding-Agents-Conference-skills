---
name: product-research
description: Use when you need to research competitors, customers, market dynamics, or stakeholders and want Claude Code to synthesize findings into actionable product insights. Requires web access or pre-gathered research input.
---

# Product Research with Claude Code

## Overview

Two-phase technique for deep product research. First, offload broad information gathering to cheaper deep-research tools (Perplexity, ChatGPT Deep Research). Then feed those raw findings into Claude Code for synthesis, gap analysis, and strategic recommendations.

**Core principle:** Claude Code with web access is like having 100 researchers on staff. Give it big, open-ended questions. Brain-dump every open question you have stream-of-consciousness. The agent thrives on breadth -- let it surprise you with what it surfaces.

**Dependency:** Web search access (Claude Code with web tools, or pre-gathered research documents to feed in).

## When to Use

- Entering a new market and need competitor landscape mapped
- Preparing for a sales call and need customer org charts, stakeholder priorities, and pain points
- Evaluating build-vs-buy decisions and need feature comparisons across vendors
- Running a quarterly strategy review and need market trends synthesized
- Exploring a new product direction and have dozens of unanswered questions

## When NOT to Use

- You need a single factual answer (just search directly)
- The research requires proprietary databases or paywalled sources Claude cannot access
- You need legally verified claims (agent research is a starting point, not a legal opinion)

## Common Mistakes

| Mistake | Why it's wrong |
|---------|---------------|
| Asking narrow, specific questions one at a time | You lose the agent's biggest strength: parallel exploration. Dump all your open questions at once and let it find connections you would not have thought of. |
| Running expensive Claude Code tokens on raw information gathering | Deep research tools like Perplexity and ChatGPT are cheaper for the gathering phase. Use Claude Code for the synthesis and strategic thinking, not the initial web crawling. |
| Treating agent output as verified fact | The agent surfaces leads and patterns. Always verify critical claims -- competitor pricing, customer org details, market size figures -- before acting on them. |
| Skipping the brain-dump and writing a polished brief instead | The messier and more complete your question dump, the better. The agent handles ambiguity well. A polished brief often omits the half-formed questions that lead to the best insights. |

## Phase 1: Cheap Deep Research (Gather)

Use Perplexity, ChatGPT Deep Research, or similar tools for raw information gathering. This saves tokens and leverages tools purpose-built for web-scale search.

### Step 1: Brain-dump your open questions

Write every question you have, stream-of-consciousness. Do not edit for clarity or organization. The goal is completeness, not polish.

**Example brain-dump prompt for a deep research tool:**

```
I'm building a [product type] in the [industry] space. Here are all my open questions:

COMPETITORS
- Who are the top 5 players? Who's growing fastest?
- What do their customers complain about in G2/Capterra reviews?
- What's their pricing model? Any recent pricing changes?
- Who just raised funding or got acquired?
- What features do they advertise that they don't actually deliver well?

CUSTOMERS
- What job titles typically buy this kind of tool?
- What's the typical buying committee look like?
- What triggers the purchase -- what pain point becomes unbearable?
- What do they use before they buy a dedicated tool? (spreadsheets? internal tools?)

MARKET
- Is this market growing? Any analyst reports with TAM numbers?
- What adjacent markets are converging into this space?
- Any regulatory changes that affect demand?

STAKEHOLDERS (for a specific target account)
- What's [Company X]'s org structure for their [department]?
- Who reports to who? Who has budget authority?
- What tech stack are they currently using? Any job postings that reveal tools?
- Have they spoken at conferences about their pain points?

Just dump everything you find. Don't summarize yet. I want raw material.
```

### Step 2: Collect the raw output

Save the deep research output to a file or set of files. Do not try to organize it yet. Raw is fine.

```
research/
  competitors-raw.md
  market-raw.md
  customer-raw.md
  stakeholder-raw.md
```

## Phase 2: Claude Code Synthesis (Analyze)

Feed the raw research into Claude Code and ask it to synthesize, find gaps, and produce strategic output.

### Step 3: Feed raw research to Claude Code with synthesis prompts

Give Claude Code the gathered material along with a clear synthesis request. This is where the agent earns its keep -- connecting dots across sources, spotting contradictions, and surfacing insights.

**Example synthesis prompt:**

```
I've attached raw research on competitors, market, and customers for [product].

Please:
1. Build a competitor comparison matrix (features, pricing, strengths, weaknesses)
2. Identify the top 3 competitor weaknesses we could exploit
3. Map the typical buying journey and identify where competitors lose deals
4. Flag any contradictions or gaps in the research that need further investigation
5. Recommend our positioning angle based on what you see
```

### Step 4: Ask for specific deep-dives

Once you have the synthesis, use Claude Code's web access to fill gaps the cheap tools missed.

```
The research didn't cover [Company X]'s recent product launches.
Search for their changelog, blog posts, and press releases from the last 6 months.
What did they ship and how does it affect our competitive positioning?
```

### Step 5: Generate deliverables

Ask Claude Code to package findings into the format you actually need.

**Research domains and their deliverables:**

| Domain | Output |
|--------|--------|
| Competitors | Feature comparison matrix, weakness analysis, positioning map |
| Customers | Buyer persona cards, buying journey map, objection-handling guide |
| Market | TAM/SAM/SOM estimates, trend summary, regulatory risk assessment |
| Stakeholders | Org chart sketch, power map, recommended outreach sequence |

### Step 6: Identify what the research could not answer

Always end with a gap analysis. Ask Claude Code:

```
What questions from my original brain-dump are still unanswered or only partially answered?
What new questions emerged from this research that I should investigate next?
```

This becomes the input for your next research cycle.

## Quick Reference

| Item | Detail |
|------|--------|
| Phase 1 tool | Perplexity, ChatGPT Deep Research, or similar (cheap, broad) |
| Phase 2 tool | Claude Code with web access (expensive, strategic) |
| Input format | Stream-of-consciousness brain-dump of all open questions |
| Raw research location | `research/*.md` or equivalent working directory |
| Key output | Synthesis documents, comparison matrices, gap analysis |
| Cost optimization | Gathering phase on cheap tools, synthesis phase on Claude Code |

## Key Principles

1. **Brain-dump, don't brief.** The messier and more complete your question list, the better the output. Treat it like you have 100 researchers -- dump every open question stream-of-consciousness.
2. **Two-phase for cost efficiency.** Cheap deep-research tools for gathering, Claude Code for synthesis. Do not burn expensive tokens on raw web crawling when purpose-built tools do it better and cheaper.
3. **Breadth before depth.** Start with all your questions at once. The agent finds connections across domains that you miss when researching one question at a time.
4. **The agent surfaces, you verify.** Treat output as high-quality leads, not verified facts. Competitor weaknesses, org charts, stakeholder info -- always confirm before acting.
5. **Research is iterative.** Every synthesis reveals new gaps. End each cycle by identifying unanswered questions and feeding them back in.

## Attribution

Based on techniques from Rob and Omeh at the Coding Agents: AI Driven Dev Conference. Rob advocates treating Claude Code like having 100 researchers and brain-dumping all open questions stream-of-consciousness. Omeh recommends using cheaper deep research tools (Perplexity, ChatGPT) first to save tokens, then feeding the gathered plan into Claude Code for synthesis.
