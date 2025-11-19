# Lesson Prompt: Codex Web Interface Workflows

## Lesson goal
Create a foundational 35–40 minute lesson that teaches learners how to leverage the Codex / ChatGPT web interface for research, planning, and documentation workflows inside this repository. The lesson must turn the high-level capabilities described in `docs/codex_interfaces_guide.md` into actionable guidance that complements the existing CLI lesson.

## Context to reference
- `docs/codex_interfaces_guide.md` for capability descriptions (mini briefs, context chunking, browser tips).
- `references/architecture/` and `docs/workflow_patterns.md` for realistic research artifacts to practice with.
- Any current best practices from https://developers.openai.com/docs/guides (especially Prompt Engineering, Safety, and context window guidance) to keep the lesson aligned with the latest OpenAI recommendations.

## Required lesson sections (follow this order)
1. **Objectives** – 3–4 measurable takeaways focused on planning in the web UI (e.g., "Compose a mini brief that sets constraints for a Codex session").
2. **Introduction** – Explain why/when to choose the web interface over IDE or CLI, highlighting strengths such as brainstorming, summarization, and rapid iteration. Anchor the intro with examples pulled from the interface guide.
3. **Core Content** – Break into subsections:
   - *Session setup* – Crafting mini briefs, pinning repo constraints, and importing snippets from files. Include screenshots callouts or markdown instructions referencing ChatGPT features like pinned instructions and context file uploads where applicable.
   - *Managing long conversations* – Walkthrough of recap bullets, numbered checkpoints, and when to prune context. Tie back to developer docs on context windows and tokens.
   - *Applying to repo workflows* – Demonstrate planning a feature using references from `references/` and mapping outcomes to `docs/` or `lessons/` updates.
   Each subsection should include step-by-step instructions and example prompts (quote-format) readers can copy.
4. **Exercises** – At least two practice tasks. One should have learners run a two-step planning conversation with recap bullets and open questions; another should require turning a web UI brainstorm into a saved summary under `references/session_logs/`.
5. **Troubleshooting** – Common pitfalls such as browser session resets, rate limits, or losing context. Include guidance from the OpenAI docs on handling token limits and safeguarding sensitive data.
6. **Resources** – Bullet list linking to internal files, OpenAI docs, and relevant agents (e.g., Workflow Architect, Prompt Librarian) that enhance web sessions.

## Tone & formatting requirements
- Use encouraging, instructor-style prose with actionable verbs ("craft," "summarize," "transfer").
- Include inline callouts for best practices (e.g., `> Tip: ...`).
- Reference specific repo paths whenever you cite files or logs so learners know where to click.
- Emphasize logging outcomes into `references/session_logs/` to reinforce knowledge capture.

Deliver the final lesson as `lessons/interfaces/01_codex_web_workflows.md` (the prompt should remind the next author to use that filename).
