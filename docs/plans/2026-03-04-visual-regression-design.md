# Visual Regression Testing Skill — Design

**Source**: Rob's talk at Coding Agents Conference [03:20:25 - 03:22:07]
**Skill Name**: `visual-regression`
**Status**: Approved, ready for implementation
**Dependency**: Playwright (must be installed in the project)

---

## Executive Summary

A Claude Code skill with two modes that automates visual QA for user-facing changes. During development (`document` mode), the agent creates Playwright screenshot walkthroughs whenever it makes UI changes. At release time (`compare` mode), it generates screenshots at two release tags, pixel-diffs them, and uses a sub-agent to classify changes as expected or unexpected, prioritizing what humans should review.

---

## Mode 1: `document` (During Development)

Triggered when the agent makes a user-facing change.

### What it does:
1. Identifies all affected user flows based on the changes made
2. Creates a Playwright test script that captures a sequence of screenshots for each flow
3. Writes a textual walkthrough alongside each screenshot describing what the user sees and what changed
4. Saves screenshots to `.screenshots/flows/` (gitignored — regenerable)
5. Saves the walkthrough manifest as `.screenshots/manifest.json`

### Manifest structure:
```json
{
  "flows": [
    {
      "name": "login-flow",
      "description": "User login from landing page to dashboard",
      "screenshots": [
        {
          "file": "flows/login-flow/01-landing-page.png",
          "description": "Landing page with login button visible",
          "step": "Navigate to /"
        },
        {
          "file": "flows/login-flow/02-enter-credentials.png",
          "description": "Login form with email and password fields",
          "step": "Click login button"
        }
      ],
      "introduced_by": "commit abc1234 — Add social login buttons",
      "pr": "#42"
    }
  ]
}
```

### Key decisions:
- Screenshots are dev files, NOT committed to git (they're regenerable)
- `.screenshots/` directory is added to `.gitignore`
- Manifest IS committed — it's the lightweight record of what flows exist
- Playwright scripts are committed under `e2e/visual/` so they can be rerun

---

## Mode 2: `compare` (At Release Time)

Triggered manually when preparing a release.

### What it does:
1. Takes two git refs as input (e.g., `v1.2.0` and `v1.3.0`, or a tag and `HEAD`)
2. Checks out the baseline ref (previous release tag)
3. Runs all Playwright screenshot scripts from `e2e/visual/`, saves to `.screenshots/baseline/`
4. Checks out the current ref (new release tag or HEAD)
5. Runs the same scripts, saves to `.screenshots/current/`
6. Runs pixel diff between baseline and current for each screenshot
7. For every screenshot that differs, spawns a sub-agent that:
   - Examines both images (baseline vs current)
   - Reads the merged PRs/commits between the two refs (`git log baseline..current`)
   - Classifies the change as **expected** (matches a merged PR's intent) or **unexpected** (possible regression)
   - Assigns a risk level: **high** (unexpected change), **medium** (expected but large), **low** (expected and minor)
8. Outputs a prioritized report at `.screenshots/report.md`

### Report structure:
```markdown
# Visual Regression Report
**Baseline**: v1.2.0 | **Current**: v1.3.0
**Date**: 2026-03-04
**Total screenshots**: 47 | **Changed**: 12 | **Unchanged**: 35

## High Risk (needs human review)
### checkout-flow/03-confirmation.png
- **Risk**: HIGH — Unexpected change
- **What changed**: Payment total formatting changed from $X.XX to $X
- **Related PRs**: None found that mention payment formatting
- **Recommendation**: Investigate before release

## Medium Risk
...

## Low Risk (expected changes)
...
```

### Key decisions:
- Does NOT run in CI (too slow, per Rob's advice)
- Runs on a local machine or dedicated build box at release time only
- Uses `pixelmatch` or similar for diffing (the skill will check what's available)
- Sub-agent analysis uses Claude's vision capabilities to interpret screenshot differences

---

## File Structure

```
project/
  .screenshots/           # gitignored
    manifest.json          # committed — maps flows to screenshots
    flows/                 # generated screenshots during dev
      login-flow/
        01-landing-page.png
        02-enter-credentials.png
      checkout-flow/
        01-cart.png
        02-payment.png
    baseline/              # generated at compare time (old release)
    current/               # generated at compare time (new release)
    diffs/                 # pixel diff output
    report.md              # comparison results
  e2e/
    visual/                # committed — Playwright scripts
      login-flow.spec.ts
      checkout-flow.spec.ts
```

---

## What This Skill Does NOT Do

- Run in CI (too slow)
- Commit screenshots to git (they're regenerable)
- Replace manual QA entirely — it prioritizes what humans should look at
- Handle non-visual changes (API-only changes, backend logic)
- Set up Playwright from scratch (assumes it's already installed)

---

## Skill Invocation

```
/visual-regression document   # after making UI changes
/visual-regression compare v1.2.0 v1.3.0   # at release time
```

---

## Attribution

Based on Rob's technique shared at the Coding Agents: AI Driven Dev Conference [03:20:25 - 03:22:07]. Rob uses this pattern across multiple projects and calls it a "massive accelerant" for release QA.
