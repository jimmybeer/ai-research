# Lesson Prompt: Multi-Interface Workflow Handoffs

## Lesson goal
Author an advanced (~60 minute) lesson that teaches contributors how to orchestrate work across the Codex web UI, VS Code extension, and CLI in one cohesive flow. The lesson should operationalize the decision matrix and handoff guidance inside `docs/codex_interfaces_guide.md`, demonstrating how to summarize progress, switch contexts, and log outputs across interfaces.

## Context to reference
- `docs/codex_interfaces_guide.md` – especially the interface selection matrix and multi-surface walkthrough.
- `workflows/` directory for example automation scripts, plus `scripts/` for any export utilities (e.g., `scripts/export_outline.sh`).
- `lessons/using_codex_cli_basics.md` and the forthcoming web/IDE lessons so readers can connect prior knowledge.
- Up-to-date orchestration and safety guidance from https://developers.openai.com/docs/guides (planning, evaluation, safety, and API limits) to explain why/when to switch surfaces.

## Required lesson sections (follow this order)
1. **Objectives** – 4+ outcomes such as evaluating which interface fits a task, creating portable handoff summaries, and executing a three-stage workflow (web → IDE → CLI).
2. **Introduction** – Describe the pain points this lesson solves (context loss, duplicated effort) and preview the case study learners will complete. Mention prerequisite lessons.
3. **Core Content** – Structure into four subsections:
   - *Decision matrix deep dive* – Walk through real repo scenarios (brainstorming docs, refactoring scripts, running tests). Include a table referencing `docs/codex_interfaces_guide.md` plus cues from OpenAI docs on context limits.
   - *Case study walkthrough* – Outline a sample project: plan in the web UI, implement in VS Code, validate in CLI. Provide explicit steps, prompts, and commands to run.
   - *Handoff mechanics* – Teach how to produce concise summaries, store them in `references/notes/hand-off.md` or `references/session_logs/`, and maintain consistent agent instructions. Include templates for summary bullets and checklists.
   - *Automation boosters* – Highlight scripts or workflows (`scripts/export_outline.sh`, Git hooks, etc.) that ease transitions. Encourage documenting run logs in `references/session_logs/`.
4. **Exercises** – Require learners to repeat the case study with their own lightweight feature, forcing at least two interface switches. Include a retrospective template they must fill out, plus a stretch goal integrating the Codex Interface Advisor Agent.
5. **Troubleshooting** – Cover common pitfalls: forgetting to sync instructions across surfaces, stale branches between IDE/CLI, mismatched context windows, or missing logs. Reference OpenAI docs for rate limits and context resets.
6. **Resources** – Provide links to internal docs, agents, prompts, and relevant developer documentation on interface best practices.

## Tone & formatting requirements
- Strategic, systems-thinking voice that still provides actionable steps.
- Use diagrams or ASCII flowcharts if possible to show the three-step workflow.
- Include `> Handoff Checklist` callouts summarizing what to capture before switching interfaces.

Remind the final lesson author to store the completed lesson at `lessons/workflows/01_multi_interface_handoff.md` and update `lessons/README.md` with its metadata.
