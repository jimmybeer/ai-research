# Prompt: README Generator

## Metadata
- **Name:** README Generator
- **Category:** Documentation
- **Purpose:** Produce a high-quality README covering overview, setup, usage, and contribution notes.
- **When to use:** Kickstarting a new project or refreshing outdated documentation.
- **Best interface:** Web (for longer drafts) or CLI (to save output directly to file).
- **Estimated time:** 8–12 minutes per README.

## Prompt Text
```
You are a meticulous technical writer tasked with generating a README for the project described below.

Project summary:
[Describe project purpose, tech stack, audience]

Required sections (in order):
1. Title and one-line elevator pitch.
2. Status badge or maturity note.
3. Table of Contents (optional if README < 30 lines).
4. Overview (what problem it solves, key features).
5. Quick Start (setup steps, commands).
6. Usage Examples (code snippets or CLI commands).
7. Configuration / Environment variables.
8. Testing / QA instructions.
9. Contribution guide (or link to docs).
10. License and acknowledgements.

Formatting rules:
- Use Markdown heading levels properly.
- Provide fenced code blocks for commands.
- Highlight placeholders in `[brackets]` and explain how to replace them.
- Keep tone professional but approachable.

Input data:
[Paste notes, project specs, or existing README snippets]
```

## Customization Guide
- Add/remove sections by editing the “Required sections” list.
- For multi-language projects, include a matrix under “Usage Examples”.
- Insert company or personal branding by adding a “Credits” section.

**Variations:**
- *Template mode:* Replace “Input data” with `docs/template.md` to standardize outputs.
- *Mini README:* Drop Table of Contents and combine sections 5–7 into “Quick Start & Configuration”.
- *API focus:* Add “API Reference” section with link placeholders.

## Usage Example
```bash
codex chat -p prompts/documentation/readme_generator.md --context references/project_notes.md > README_draft.md
```
**Expected output:** A fully formatted README saved to `README_draft.md`. Review, edit, then move to project root.

## Tips
- Provide actual commands and environment variable names in the input to reduce guesswork.
- Use `--temperature 0.3` for more deterministic documentation.
- After generating, run markdownlint or paste into VS Code preview for QA.

## Related Resources
- [`lessons/using_codex_cli_basics.md`](../../lessons/using_codex_cli_basics.md)
- [`agents/repo_teacher.agent.md`](../../agents/repo_teacher.agent.md)
- [`docs/contributing.md`](../../docs/contributing.md)
- Cheatsheet: [`cheatsheets/codex_cli_commands.md`](../../cheatsheets/codex_cli_commands.md)
