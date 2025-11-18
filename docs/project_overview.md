# Project Overview

## Vision and Goals
This repository is the canonical, personal knowledge base for mastering ChatGPT Codex across web, IDE, and CLI interfaces. It captures proven workflows, vetted prompts, agents, and references so Codex can be on-call for daily development, planning, and documentation work without starting from scratch. The overarching goal is to build a living system that helps me:
- Launch Codex-powered automations in seconds.
- Preserve institutional memory about what worked (and why).
- Teach future-me how to approach new problems with ready-made playbooks.

## Content Types
- **Lessons** – structured learning paths and step-by-step guides that demonstrate how to achieve concrete outcomes (Phase 3).
- **Cheat sheets** – concise reminders, tables, and code snippets for fast lookup (Phase 3).
- **Prompts** – reusable templates tailored to repetitive tasks like reviews, documentation generation, testing, requirements management, and architecture planning.
- **Agents** – `.agent.md` briefs that encode roles, capabilities, and guardrails for Codex (Phase 2).
- **Scripts** – helper utilities or shell snippets that pair with prompts to execute workflows end-to-end.
- **References** – curated links, highlight summaries, and personal notes.
- **Workflows** – end-to-end blueprints that combine prompts, agents, and scripts to solve recurring problems (Phase 3).

## Multi-interface Codex usage
- **Web** – Ideal for exploratory conversations; link directly to prompts or lessons and let Codex read the surrounding context.
- **VS Code** – Best for in-place code modifications, refactors, or doc authoring. Agents stored in `agents/` can be invoked as tasks within the editor.
- **CLI** – Perfect for scripted runs, batch edits, and automation experiments. Pair CLI sessions with `scripts/` and `workflows/` to replay reliable steps.

## Philosophy and Design Principles
1. **Practical first** – Every artifact must solve a real scenario (reviews, docs, testing, planning, design).
2. **Modular building blocks** – Prompts, agents, and workflows should be remixable; avoid monolithic write-ups.
3. **Explain the why** – Notes and references describe rationale, not just steps, so future iterations are easier.
4. **Codex-ready formatting** – Markdown with clear headings, numbered steps, and explicit inputs/outputs makes it easier for Codex to parse.
5. **Single-source truth** – The repo is authoritative; external docs should be imported or linked from `references/`.

## Differentiators
- Focused on Codex-powered productivity rather than general AI notes.
- Structured to support daily reuse by a single user, yet still formal enough for PR review and long-term maintenance.
- Treats Codex agents as first-class citizens; workflows describe which interface (web, IDE, CLI) is optimal for each task.

## Roadmap
### Phase 1 – Foundation (current)
Repository scaffolding, docs, structure, and placeholders for future content.

### Phase 2 – Agent system
Build at least four agents, document how to drive them from each interface, and provide a getting-started walkthrough for running agents end-to-end. (See this section for cross-links once shipped.)

### Phase 3 – Starter content
Seed lessons, cheat sheets, prompt packs, and workflow exemplars covering git workflows, documentation generation, test automation, requirements management, project planning, architecture design, and coding support.

### Phase 4 – Polish and extensions
Add review automation, richer templates, metrics tracking, and ideas for future experiments or integrations.
