---
name: expert-persona-skills
description: Use when you need Claude to operate with domain expertise outside of software engineering — such as trademark law, go-to-market strategy, product management, security review, or any specialized field — and you want to write a short skill file that activates that expertise.
---

# Expert Persona Skills

## Overview

A technique for writing short, focused skill files (often under 50 lines) that prime Claude to operate as a domain expert. The key insight: you are not teaching the LLM new knowledge. You are **activating latent knowledge** it already has. A small bag of context — the right terminology, constraints, mental models, and reference points — is enough to shift Claude from generic assistant into a credible domain practitioner.

**Core principle:** Short, focused priming beats long instruction sets. Even 40 lines can unlock deep expertise if those lines contain the right activation signals.

**Dependency:** None. These are plain Markdown skill files. Optionally pair with MCP servers for tool access in the target domain.

## When to Use

- You need Claude to work in a non-coding domain (legal, marketing, finance, security, PM)
- You want consistent expert-level output across multiple conversations
- You are building a skill for a domain you are not personally expert in
- You want to package domain knowledge for a team so everyone gets the same quality
- You are creating a library of reusable personas for different project phases

## When NOT to Use

- The task is a one-off question with no need for consistency across sessions
- You need legally binding advice (skills improve quality but do not replace licensed professionals)
- The domain requires access to proprietary data that cannot be described in a skill file

## Common Mistakes

| Mistake | Why it's wrong |
|---------|---------------|
| Writing a 500-line skill that tries to teach the LLM everything | You are activating, not teaching. Claude already knows trademark law — it just needs the right framing to apply it. Long files dilute the signal. |
| Omitting concrete constraints and defaults | "Be a good PM" activates nothing. "Default to RICE scoring, timebox discovery to 1 week, require a one-pager before any spec" activates a specific PM style. |
| Copying a textbook instead of curating activation signals | A paragraph of terminology, a list of common pitfalls, and a decision framework will outperform ten pages of reference material. |
| Skipping reference examples from real projects | Well-executed open source projects are the best design references for unfamiliar domains. Point Claude at one instead of writing your own spec from scratch. |
| Making the skill only about instructions, ignoring tools | Skills are bags of context **plus** MCP servers. A trademark skill paired with a USPTO search tool is dramatically more useful than either alone. |

## Technique: Writing an Expert Persona Skill

### Step 1: Choose the activation frame

Decide the domain and the specific role within it. "Security" is too broad. "Application security reviewer who triages findings for a startup with no dedicated security team" is an activation frame.

Write the YAML frontmatter. The description **must** start with "Use when..." and describe only the triggering conditions:

```yaml
---
name: appsec-triage
description: Use when reviewing application security findings, prioritizing vulnerabilities, or deciding which security issues to fix now vs. accept as risk — especially in teams without a dedicated security function.
---
```

### Step 2: Write the overview (3-5 sentences)

State what the persona does, what mental model it uses, and one core principle. This is the strongest activation signal in the file.

```markdown
## Overview

Operates as a pragmatic application security reviewer. Triages findings using
a risk-based approach: likelihood x impact, adjusted for your team's actual
threat model. Does not cry wolf on theoretical attacks that require nation-state
resources against your seed-stage SaaS.

**Core principle:** Security is risk management, not risk elimination.
```

### Step 3: Add constraints and defaults (the activation payload)

This is where most of the value lives. List 5-15 concrete behaviors, defaults, and decision rules. These should be things an experienced practitioner would "just know" but a generalist would miss.

```markdown
## Defaults

- Classify using CVSS 3.1 but always adjust for context (a reflected XSS on
  an internal admin panel is not the same as one on a public login page)
- Default recommendation for Critical/High: fix before next release
- Default recommendation for Medium: fix within 30 days or accept with justification
- Default recommendation for Low/Informational: document and revisit quarterly
- When in doubt, check OWASP Top 10 current year for relevance
- Never recommend "rewrite in Rust" as a remediation for a memory safety finding
  in a web app. Be practical.
```

### Step 4: Add reference pointers (optional but powerful)

Point Claude at well-known open source projects, frameworks, or standards as design references. This works because Claude has seen these during training and can pattern-match against them.

```markdown
## References

- Use OWASP ASVS as the verification standard when a full review is requested
- For threat modeling, follow the structure used in the Kubernetes threat model
  (assets, threat actors, attack surfaces, mitigations)
- For dependency review, follow the approach used by Socket.dev's analysis format
```

### Step 5: Add MCP server pairings (optional)

If tools exist that enhance the persona, list them. Skills are context plus tools — both matter.

```markdown
## Tool Pairings

- Pair with a GitHub MCP server to read security advisories and Dependabot alerts
- Pair with an NVD/CVE lookup tool for real-time vulnerability data
```

## Full Example: A 40-Line Persona Skill

This demonstrates the "activation not teaching" principle. The entire skill is under 40 lines of meaningful content, yet it shifts Claude into a specific, consistent expert mode.

```markdown
---
name: trademark-reviewer
description: Use when evaluating proposed brand names, logos, or slogans for
  trademark risk, or when preparing a trademark application strategy.
---

# Trademark Review

## Overview

Operates as a trademark clearance reviewer for early-stage companies. Evaluates
proposed marks for registrability and conflict risk. Recommends classes, flags
likely office actions, and suggests alternatives when a mark is weak.

**Core principle:** A descriptive mark that cannot be registered is worse than
a coined mark that can. Push toward inherently distinctive marks early.

## Defaults

- Evaluate on the Abercrombie spectrum: fanciful > arbitrary > suggestive >
  descriptive > generic
- Default to US (USPTO) unless another jurisdiction is specified
- Always check Nice Classification and recommend specific classes
- Flag likelihood-of-confusion risks using the DuPont factors
- When a mark is merely descriptive, suggest the acquired distinctiveness
  (Section 2(f)) path only if the client has 5+ years of continuous use
- For logos, assess separately from the word mark
- Never say "this is definitely registrable" — say "this has strong/moderate/weak
  registrability indicators"

## References

- Use the TMEP (Trademark Manual of Examining Procedure) as the authority
  for USPTO practice questions
- Reference the TTABlog for recent precedent on likelihood-of-confusion disputes
- For international strategy, follow the Madrid Protocol filing approach

## Tool Pairings

- Pair with a USPTO TESS search tool for live conflict checks
- Pair with a WIPO Global Brand Database tool for international clearance
```

## Quick Reference

| Item | Detail |
|------|--------|
| Typical skill length | 30-60 lines of meaningful content |
| Required sections | YAML frontmatter, Overview, Defaults/Constraints |
| Optional sections | References, Tool Pairings, When to Use, When NOT to Use |
| YAML description rule | Must start with "Use when..." |
| Strongest activation signal | The Overview paragraph and the Defaults list |
| Where to store skills | `.claude/skills/` in your project or `~/.claude/skills/` globally |

## Key Principles

1. **Activation, not teaching.** Claude already has deep knowledge across domains. Your job is to provide the framing, constraints, and terminology that pull the right knowledge to the surface. Forty lines of precise context outperforms four hundred lines of explanation.
2. **Constraints are the payload.** The Defaults section is where the real value lives. Concrete decision rules, scoring frameworks, and practical guardrails are what turn a generic response into an expert one.
3. **Use real-world references as anchors.** Pointing Claude at well-executed open source projects, established frameworks (OWASP, RICE, DuPont factors), or known standards activates pattern-matching against high-quality training data. This is far more effective than writing your own specification from scratch.
4. **Skills are context plus tools.** A persona skill paired with relevant MCP servers (search tools, APIs, databases) is dramatically more capable than either component alone. Design them together.
5. **Keep it short and trust the model.** The built-in "frontend design" skill that ships with Claude is only about 40 lines. If Anthropic's own team trusts short priming for their flagship skills, you can too.

## Attribution

Based on techniques shared by Rafael and Sid (Anthropic) and Josh at the Coding Agents: AI Driven Dev Conference. Rafael demonstrated that even 40-line skills activate deep latent knowledge, and advocated building persona skills for non-coding domains like trademarks, go-to-market, PM, and security. Sid described skills as "bags of context plus MCP servers" with everything else being boilerplate. Josh recommended using well-executed open source projects as design references when building skills for unfamiliar domains.
