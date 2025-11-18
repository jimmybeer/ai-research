# Contributing Guide
Even though this is a personal knowledge base, consistent structure keeps Codex productive and future edits painless. Follow the steps below whenever you add or modify content.

## Adding content by type
- **Lessons** (`lessons/`) – Create a new folder per topic (for example `lessons/git/`) and add numbered Markdown files such as `01_basics.md`, `02_advanced.md`. Include learning objectives, prerequisites, numbered steps, and practical exercises.
- **Cheat sheets** (`cheatsheets/`) – Store short tables or checklists using descriptive names like `git_review_cheatsheet.md`. Prefer Markdown tables for quick scanning.
- **Prompts** (`prompts/`) – Organize by domain (`prompts/review/`, `prompts/testing/`). Each file should define context, instructions, input slots, and variants.
- **Agents** (`agents/`) – Use `.agent.md` extension. Capture role, capabilities, guardrails, and interface guidance. Link to related prompts/workflows.
- **Scripts** (`scripts/`) – Keep scripts lightweight (Bash, PowerShell, Python). Include inline docs plus a short usage section at the bottom. Avoid secrets or machine-specific paths.
- **References** (`references/`) – Store curated notes as Markdown; for link lists, use bullet tables with `title`, `summary`, `link`, and `tags` columns.
- **Workflows** (`workflows/`) – Document intent, triggers, dependencies, and Codex interface recommendations. Include both human steps and agent prompts.

## Naming conventions
- Use `snake_case.md` for most Markdown files (`requirements_review.md`).
- Prefix ordered lessons or experiments with zero-padded numbers (`01_baseline.md`).
- Agent files must end with `.agent.md` (`git_review.agent.md`).
- Script names should describe the action (`generate_release_notes.py`).
- Keep directory names lowercase.

## Style guidelines
- Prefer Markdown with clear headings and numbered lists for reproducibility.
- Highlight placeholders with angle brackets (for example `<repo_url>`), and explain how to replace them.
- Tag files with topic labels near the top (for example `Tags: git, testing`).
- For prompts, include sections for **Context**, **Instruction**, **Input Variables**, and **Safety Checks**.
- Lessons and workflows should call out which Codex interface (web, VS Code, CLI) is best suited for each step.

## Quality standards & review process
1. Re-read new content in VS Code preview to ensure formatting is correct.
2. Use `make lint` (once tooling is added) or at least run `markdownlint` if available.
3. Cross-link references, prompts, and workflows so Codex can traverse easily.
4. Use personal PRs even for solo work: open a branch, push changes, and self-review via GitHub or `gh pr diff` to stay disciplined.
5. Document test evidence (if scripts or automations are involved) in commit messages or the PR description.

## Templates and examples
- Refer to folder-level README files for minimal templates.
- Copy prior lessons or prompts when starting something new to maintain tone.
- Store reusable prompt skeletons in `prompts/templates/` so future prompts stay consistent.

## Git workflow
1. Create a feature branch named `feat/<topic>` or `docs/<topic>`.
2. Commit using Conventional Commit prefixes (`feat:`, `docs:`, `chore:`).
3. Open a PR (even if private) with: problem statement, bullet summary, test evidence, and links to relevant references or screenshots.
4. After review, squash-and-merge or fast-forward depending on preference, then delete the branch.
