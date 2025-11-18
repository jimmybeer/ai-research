# Workflow Patterns

Workflow patterns describe the repeatable ways Codex accelerates daily tasks. Each pattern captures intent, required context, outputs, and which interface pairs best with the steps so I can reuse them quickly.

## Common categories
- **Learning accelerators** – Guided study sessions, interactive lessons, or concept breakdowns.
- **Automation loops** – Repetitive maintenance tasks (tests, reviews, documentation checks) driven by prompts and scripts.
- **Content creation** – Generating docs, release notes, plans, or architecture diagrams.
- **Refactoring & coding** – Structured code edits, test scaffolding, or bug triage.
- **Planning & management** – Requirements alignment, roadmap drafting, backlog refinement.

## Documentation template
```
### Pattern name
- **Intent** – What this workflow accomplishes.
- **Inputs** – Files, prompts, credentials, or context required.
- **Outputs** – Artifacts produced (PR, doc, checklist, script updates).
- **Process** – Numbered steps mixing human actions and Codex prompts.
- **Best interface** – Web, VS Code, CLI, or hybrid.
- **Related resources** – Links to prompts, agents, scripts, or references.
```

## Example patterns
### Rapid Git Review Loop
- **Intent** – Perform a structured code review for medium-sized PRs with Codex assistance.
- **Inputs** – Diff link or patch file, `prompts/review/structured_review.md`, `agents/git_review.agent.md` (Phase 2), and project-specific guidelines.
- **Outputs** – Review notes Markdown, suggested fixes, and optional inline comments ready to paste.
- **Process**
  1. In VS Code, open the diff and highlight sections needing attention.
  2. Run Codex with the review agent and supply the prompt plus context paths.
  3. Iterate on Codex suggestions, capturing accepted feedback in `references/review_logs/`.
  4. Export final comments to GitHub or paste into your PR.
- **Best interface** – VS Code (tight loop with editor context).
- **Related resources** – `prompts/review/structured_review.md`, `references/git_standards.md`.

### Documentation Generation Sprint
- **Intent** – Turn existing code or meeting notes into polished documentation.
- **Inputs** – Source files, `prompts/docs/doc_gen_template.md`, `scripts/export_outline.sh`.
- **Outputs** – Draft doc stored under `references/` or `docs/`, plus checklist of gaps.
- **Process**
  1. Run the CLI script to extract headings or comments from the codebase.
  2. In the web interface, feed the extracted outline and apply the documentation prompt.
  3. Review the generated doc in VS Code, editing for accuracy.
  4. Push the doc with a `docs:` commit.
- **Best interface** – Hybrid (CLI for extraction, web for drafting, VS Code for polish).
- **Related resources** – `prompts/docs/doc_gen_template.md`, `scripts/export_outline.sh`.

### Test Automation Kickoff
- **Intent** – Create or update automated tests using Codex guidance.
- **Inputs** – Target module path, `prompts/testing/test_scaffold.md`, access to pytest/CI configuration.
- **Outputs** – Test files under `tests/`, CI notes, and captured TODOs.
- **Process**
  1. Gather requirements or bug reports from `references/`.
  2. Launch Codex in the CLI with the testing prompt and supply module paths.
  3. Apply generated changes locally, then run `pytest -m "not slow"`.
  4. Document outcomes in `workflows/testing/` with logs and follow-up items.
- **Best interface** – CLI (tight cycle with terminal output).
- **Related resources** – `prompts/testing/test_scaffold.md`, `scripts/run_fast_tests.sh`.

> Phase 2 will introduce the agent system so each workflow can reference concrete `.agent.md` files. Phase 3 will seed detailed walkthroughs based on these patterns.
