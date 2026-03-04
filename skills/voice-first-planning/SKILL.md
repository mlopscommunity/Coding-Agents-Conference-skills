---
name: voice-first-planning
description: Use when starting a new feature, writing a spec, or brainstorming architecture and you want to capture richer intent than typing allows. Speak your thoughts into a transcription tool, then feed the raw transcript to Claude Code for structuring.
---

# Voice-First Planning

## Overview

Use speech-to-text tools to dictate your initial specs, feature ideas, and architectural thoughts instead of typing them. Speaking naturally produces longer, more context-rich input because people self-edit heavily when typing but ramble freely when talking. That rambling is gold — LLMs are excellent at extracting structured meaning from unstructured speech.

**Core principle:** Speaking freely captures intent that is hard to express in typed text. Don't self-edit — ramble and let the LLM find the structure.

**Dependency:** A speech-to-text tool (WhisperFlow, macOS Dictation, or similar).

## When to Use

- At the start of a new feature when you have a rough idea but haven't formalized it
- During brainstorming when you want to explore multiple approaches quickly
- When writing specs, PRDs, or design documents from scratch
- When you catch yourself staring at a blank prompt, unsure how to phrase what you want
- When explaining a bug or problem you understand intuitively but struggle to articulate in text

## When NOT to Use

- During active implementation (typing precise code instructions is faster)
- For short, well-defined commands ("fix the typo on line 42")
- When you are in a shared/quiet workspace without a private space to speak
- For editing or refining an already-written spec (just edit the text directly)

## Common Mistakes

| Mistake | Why it's wrong |
|---------|---------------|
| Editing yourself while speaking | The whole point is to capture raw, unfiltered intent. Self-editing while speaking defeats the purpose — you lose the same context you lose when typing. Just talk. |
| Skipping the transcription review | Speech-to-text makes errors. Quickly scan the transcript for mangled names, technical terms, or homophones before pasting it in. A 10-second scan prevents confused output. |
| Using voice during implementation | Voice shines during planning and ideation. Once you are writing code, typed instructions are more precise. Don't force voice where typing is better. |
| Pasting the transcript without a framing prompt | Claude Code needs to know what to do with the wall of text. Always prepend a short instruction like "Structure this into a feature spec" or "Extract the requirements from this transcript." |
| Speaking in short, clipped sentences | You are not typing. Speak in full, natural paragraphs. Explain the *why*, the context, the constraints, the edge cases. Longer is better — the LLM will compress it. |

## The Workflow

### Step 1: Set up a speech-to-text tool

Pick one and install it:

| Tool | Platform | Notes |
|------|----------|-------|
| [Wispr Flow](https://wisprflow.ai) | macOS, Windows, iOS, Android | AI-powered voice-to-text with auto-editing. 4x faster than typing. Recommended. |
| macOS Dictation | macOS | Built-in. Press Fn Fn (or Globe key twice) in any text field. Good enough for most use cases. |
| [Superwhisper](https://superwhisper.com) | macOS | Polished Whisper app with hotkey activation. |
| Windows Voice Typing | Windows | Press Win+H. Built-in, decent quality. |
| Google Docs Voice Typing | Browser | Tools > Voice typing. Works well, requires Chrome. |

Any tool that converts speech to editable text works. The key requirement is that you can paste the output into a terminal or editor.

### Step 2: Speak your idea freely

Open your transcription tool and start talking. Cover:

- **What** you want to build and **why** it matters
- **Who** will use it and what their workflow looks like
- The **constraints** — what you cannot change, what is already decided
- **Edge cases** you are already thinking about
- Anything you are **unsure** about — name the uncertainty out loud

Do not organize your thoughts first. Do not outline. Just talk. Aim for 1-3 minutes of continuous speech. This typically produces 200-500 words of transcript, which is far more context than most people would type.

### Step 3: Quick-scan the transcript for errors

Speech-to-text tools mangle technical terms. Before pasting, scan for:

- **Variable/function names** — "getUserById" might become "get user by ID" or worse
- **Library names** — "Playwright" might become "play right"
- **Homophones** — "route" vs "root", "cache" vs "cash"
- **Jargon** — domain-specific terms the model may not have in its vocabulary

Fix only the obviously wrong terms. Do not rewrite — the raw, spoken style is the point.

**Tip:** Use TMUX with VIM keybindings to quickly jump through the transcript and fix transcription errors before pasting. VIM's word-motion keys (`w`, `b`, `cw`) make surgical fixes fast.

### Step 4: Paste into Claude Code with a framing prompt

Prepend a one-line instruction that tells Claude Code what to produce:

```
Structure this spoken transcript into a feature spec with requirements,
constraints, and open questions:

[paste transcript here]
```

Other useful framing prompts:

- "Extract the architectural decisions from this transcript and list the trade-offs for each."
- "Turn this into a task breakdown with estimated complexity for each item."
- "Identify the requirements, assumptions, and risks in this transcript."
- "Summarize the core idea in 2 sentences, then list all the details I mentioned."

### Step 5: Iterate on the structured output

Claude Code will return a well-organized version of your rambling thoughts. Now you can:

- Remove sections that were tangents
- Add precision where the spoken version was vague
- Ask follow-up questions about parts the LLM flagged as ambiguous
- Feed the structured spec back into your planning workflow

This is where the real leverage appears: you went from a blank prompt to a structured spec in under 5 minutes, and it contains context you never would have typed.

## Quick Reference

| Item | Details |
|------|---------|
| Recommended tool (macOS) | WhisperFlow or macOS Dictation (Fn Fn) |
| Recommended tool (Windows) | Windows Voice Typing (Win+H) |
| Ideal speaking length | 1-3 minutes (~200-500 words of transcript) |
| Best stage to use | Planning, ideation, spec writing |
| Worst stage to use | Active implementation, precise code edits |
| Transcript editing | TMUX + VIM mode for quick surgical fixes |
| Key framing prompt | "Structure this spoken transcript into a feature spec with requirements, constraints, and open questions:" |

## Key Principles

1. **Typing makes you self-edit. Speaking does not.** When you type, you delete and rephrase to sound "right." When you speak, you explain what you actually mean, including the messy context that matters most.
2. **LLMs are excellent at extracting structure from rambling speech.** You do not need to organize your thoughts before speaking. That is the LLM's job. Your job is to provide maximum raw signal.
3. **Voice is for planning, not implementation.** This technique is most effective in the ideation and spec-writing phase. Once you are deep in code, typed instructions give you the precision you need.
4. **Fix transcription errors, but do not rewrite.** A quick scan for mangled technical terms is essential. Rewriting the transcript into polished prose is counterproductive — you are just re-introducing the self-editing problem.
5. **Always frame the paste.** A raw transcript dump without a prompt like "structure this into a spec" forces the LLM to guess what you want. One sentence of framing turns a wall of text into useful output.

## Attribution

Based on Josh's technique from the Coding Agents: AI Driven Dev Conference. Josh uses WhisperFlow to speak initial specs, noting that speaking gives more context than typing because people naturally self-edit when they type. He also recommends TMUX with VIM mode for quickly fixing transcription errors before feeding the text to an LLM.
