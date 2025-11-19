# Lesson Prompt: Codex IDE Pairing in VS Code

## Lesson goal
Develop an intermediate (≈50 minute) lesson that walks contributors through configuring and using the ChatGPT/Codex VS Code extension for inline edits, chat-driven reviews, and safe change management. The lesson should transform the guidance in `docs/codex_interfaces_guide.md` (lines describing IDE workflows) into hands-on steps that pair coding tasks with Codex assistance.

## Context to reference
- `docs/codex_interfaces_guide.md` – IDE setup instructions, inline edit workflow, chat panel guidance.
- `agents/` directory and `prompts/` catalog – highlight how to reference helper agents (Prompt Librarian, Workflow Architect) from inside the IDE chat.
- `docs/contributing.md` and `lessons/using_codex_cli_basics.md` for existing conventions on objectives/exercises and to contrast CLI workflows.
- Latest IDE integration tips from https://developers.openai.com/docs (especially sections on API keys, file context limits, and safety) to ensure the lesson mirrors current capabilities.

## Required lesson sections (follow this order)
1. **Objectives** – 3–5 skills such as authenticating the extension, invoking inline completions, reviewing diffs, and logging Codex-assisted edits.
2. **Introduction** – Briefly motivate why VS Code + Codex enables faster implementation cycles after planning in the web UI. Mention prerequisites (extension installed, repo cloned).
3. **Core Content** – Organize into three subsections:
   - *Environment setup* – Installing/authorizing the extension, enabling workspace file access, configuring hotkeys, and storing API keys securely.
   - *Inline edit workflow* – Step-by-step process for highlighting code, requesting changes, reviewing proposed diffs, and staging edits. Include safety tips (create temp branches, use `git diff`).
   - *Chat panel strategies* – Show how to contextually reference files (`@file` or copy/paste), ask for tests, and blend inline edits with chat clarifications. Encourage structured breadcrumb updates so Codex tracks the active file path.
   Each subsection should specify concrete actions, sample prompts, and references to relevant repo files (e.g., practice on `cheatsheets/` or `scripts/`).
4. **Exercises** – Provide at least two guided labs: (a) configure the extension and capture a screenshot or log verifying the setup, (b) complete a mini refactor with inline edits + chat, documenting the before/after diff and recording learnings in `references/session_logs/IDE_practice.md`.
5. **Troubleshooting** – Address authentication failures, context access limitations, extension crashes, and how to fall back to CLI if inline edits misbehave. Pull recommendations from OpenAI developer docs for rate limits and log hygiene.
6. **Resources** – List internal references (`docs/codex_interfaces_guide.md`, `cheatsheets/`), OpenAI IDE documentation, and recommended agents/prompts.

## Tone & formatting requirements
- Instructional yet pragmatic voice that assumes readers already know Git basics.
- Use numbered lists for workflows and include `> Safety Check:` callouts where irreversible edits could occur.
- Reinforce best practices like creating throwaway branches and running tests locally after Codex edits.

Remind the lesson author to save the final lesson as `lessons/interfaces/02_codex_ide_pairing.md` and to update `lessons/README.md` after drafting.
