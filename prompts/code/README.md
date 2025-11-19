# Code Prompts
Use this folder for prompts that analyze, refactor, or validate code. These prompts often pair with the Workflow Architect or Prompt Librarian agents when building automation loops.

## Available prompts
| Prompt | Description | Best Interface |
| --- | --- | --- |
| [`code_review_checklist.md`](code_review_checklist.md) | Structured PR review covering summaries, bug checks, and follow-ups. | CLI / IDE |

## Common use cases
- Pre-PR self reviews using `git diff | codex chat -p prompts/code/code_review_checklist.md`.
- Automating nightly code sweeps via shell scripts under `scripts/`.
- Pair programming sessions where Codex highlights risky changes live in VS Code.

When adding new code prompts, include guardrails for destructive actions and reference related tests or workflows.
