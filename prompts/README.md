# Prompt Library
Prompts are reusable templates that encapsulate context, instructions, and safety checks for Codex. Organize them by domain to make discovery simple.

## Category structure
- `prompts/code/` – code reviews, refactors, testing helpers.
- `prompts/documentation/` – README generators, release notes, architecture write-ups.
- `prompts/learning/` – concept explainers, study plans, onboarding aids.
- Future categories: `requirements/`, `planning/`, `qa/`.

## Choosing the right prompt
1. Identify the task type (code, docs, learning, planning).
2. Pick the category and skim README to see available prompts.
3. Review the metadata block (purpose, best interface, estimated time).
4. Customize placeholders in `[brackets]` before running.
5. Log outcomes under `references/session_logs/` for reuse.

## Prompt index
| Category | Prompt | Purpose |
| --- | --- | --- |
| Code | [`code/code_review_checklist.md`](code/code_review_checklist.md) | Structured PR review covering bugs, style, and follow-ups. |
| Documentation | [`documentation/readme_generator.md`](documentation/readme_generator.md) | Generate a comprehensive README with required sections. |
| Learning | [`learning/concept_explainer.md`](learning/concept_explainer.md) | Explain complex topics with multiple styles and learning paths. |

## Customizing prompts
- Update the “Customization Guide” section inside each prompt to suit your workflow.
- For recurring tweaks, duplicate the prompt file (e.g., `code_review_backend.md`) and note the specialization.
- Pair prompts with agents when you need persona-driven context (e.g., Prompt Librarian + documentation prompts).

## Contributing new prompts
1. Copy an existing prompt file as a template.
2. Fill out metadata, prompt text, customization guide, usage example, tips, and related resources.
3. Place the file in the correct category folder and update both this README and the category-specific README.
4. Reference relevant agents, lessons, or workflows so prompts stay connected to the knowledge base.
