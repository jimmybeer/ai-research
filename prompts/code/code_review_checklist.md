# Prompt: Code Review Checklist

## Metadata
- **Name:** Code Review Checklist
- **Category:** Code Quality / Review
- **Purpose:** Guide Codex to perform a focused review on diffs or files, highlighting bugs, style issues, and follow-up tasks.
- **When to use:** Before submitting or merging changes, or when triaging a teammate's PR.
- **Best interface:** CLI (for piping diffs) or IDE chat for inline context.
- **Estimated time:** 5–7 minutes per review.

## Prompt Text
```
You are the Code Review Checklist assistant. Review the provided code diff or file snippet using the following structure:

Context:
- Repository: [name]
- Feature/bugfix summary: [short description]
- Risk level: [low/medium/high]

Instructions:
1. Summarize the change in 2 sentences.
2. Identify potential bugs or regressions.
3. Flag style, documentation, or testing gaps.
4. List high-priority questions or blockers for the author.
5. Provide concrete improvement suggestions (code or tests).

Rules:
- Cite specific lines or functions when possible.
- Prefer actionable feedback over generic advice.
- If the diff is clean, state "No blocking issues" but still mention at least one quality assurance idea.

Input diff or file:
[Paste diff or file content here]
```

## Customization Guide
- Replace `[name]`, `[short description]`, and `[risk level]` to orient Codex.
- For large PRs, run the prompt per file and collect outputs in `references/review_logs/`.
- Add domain-specific checks (security, accessibility) under “Instructions” when needed.

**Variations:**
- *Minimal review:* Remove sections 4–5 when time is tight.
- *Deep dive:* Add “Explain the reasoning behind each risk” for critical code.
- *Pair review:* Ask for “questions to discuss live” to prep meetings.

## Usage Example
**Command:**
```bash
git diff HEAD~1 src/module.py | codex chat -p prompts/code/code_review_checklist.md --label "module-review"
```
**Expected output (excerpt):**
- Summary, bug list, style notes, and follow-up questions.
- Table or bullet list referencing line numbers.

**Interpretation:** Use the bullet list as your PR comment draft. Copy high-priority items into GitHub review or issues.

## Tips
- Keep diffs under ~300 lines; split large ones into multiple runs.
- Pair with `agents/workflow_architect.agent.md` to embed this prompt into a workflow.
- Iterate by feeding Codex’s own feedback back into a second pass (“Re-check after applied fixes”).

## Related Resources
- [`agents/workflow_architect.agent.md`](../../agents/workflow_architect.agent.md)
- [`docs/workflow_patterns.md`](../../docs/workflow_patterns.md)
- [`workflows/testing/nightly_checks.md`](../../workflows/) *(create as needed)*
- Other prompts: `prompts/documentation/readme_generator.md`, `prompts/learning/concept_explainer.md`
