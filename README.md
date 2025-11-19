# AI Research Codex Knowledge Base

> **Status:** Phase 1 – Foundation

## Purpose
This repository is my long-term, Codex-driven knowledge base for automations, prompts, reusable workflows, and practical lessons. Everything is tuned for daily referencing, fast retrieval, and incremental growth so I can onboard Codex (web, VS Code, CLI) into any task without reinventing the wheel.

## Using this repo with ChatGPT Codex
### Web interface
Paste prompt templates or lesson snippets directly into ChatGPT Codex on the web, and keep links to relevant files ready so the agent can reference them quickly. Use the `references/` directory to point Codex to supporting context before asking for help.

### VS Code integration
Open this repo in VS Code with the Codex extension or ChatGPT sidebar, then highlight any file or folder to let Codex reason over it. The `agents/` directory defines reusable `.agent.md` briefs that Codex can run in-editor to scaffold reviews, documentation, or tests.

### CLI workflow
From the Codex CLI (running in WSL), stream prompts from `prompts/`, execute helper scripts in `scripts/`, and ask Codex to modify files directly. Keep command history or shell snippets in `workflows/` so Codex agents can replay proven automations.

## Repository layout
- `docs/` – project overview, contribution guidance, and workflow references.
- `lessons/` – structured, step-by-step guides (Phase 3).
- `cheatsheets/` – quick reference tables and short reminders (Phase 3).
- `prompts/` – reusable prompt templates and patterns.
- `agents/` – Codex agent definitions (`*.agent.md`) for recurring tasks (Phase 2).
- `scripts/` – helper scripts or command snippets that pair with Codex prompts.
- `references/` – curated articles, personal notes, and link collections.
- `workflows/` – end-to-end examples of Codex-driven processes (Phase 3).

## Getting started
1. Clone the repo and open it in VS Code or your preferred terminal.
2. Read `docs/project_overview.md` to understand the vision and roadmap.
3. Skim `docs/contributing.md` for naming conventions and style rules before adding content.
4. Drop any immediate prompts or notes into the relevant directories, using the template patterns in each folder's README.

## Navigation guide
- Use the folder-level README files to understand how to organize new entries.
- Each prompt, lesson, or workflow should link back to related references and agents for quick cross-navigation.
- Search via VS Code or `rg` for tags like `#workflow`, `#prompt`, or topic-specific keywords to jump to relevant assets.
- When working in Codex, supply file paths (for example `prompts/review/quick_review.md`) so the agent can open them instantly.

## Try it now
- [Lesson: Using Codex CLI Basics](lessons/using_codex_cli_basics.md) – configure the CLI, run prompts/agents, and log results.
- [Cheatsheet: Codex CLI Commands](cheatsheets/codex_cli_commands.md) – copy/paste-ready commands and troubleshooting tips.
- Prompts to experiment with:
  - `prompts/code/code_review_checklist.md`
  - `prompts/documentation/readme_generator.md`
  - `prompts/learning/concept_explainer.md`

## Quick start
- Follow the [Getting Started Walkthrough](docs/getting_started_walkthrough.md) for three guided exercises (web, IDE, CLI).
- Run the Repository Teacher Agent to convert your first CLI session log into a lesson draft.
- Use the Codex CLI cheatsheet side-by-side while working through the lesson.

## Content overview
| Category | Highlights |
| --- | --- |
| Lessons | [`lessons/using_codex_cli_basics.md`](lessons/using_codex_cli_basics.md) |
| Cheatsheets | [`cheatsheets/codex_cli_commands.md`](cheatsheets/codex_cli_commands.md) |
| Prompts | Code: `code_review_checklist`, Docs: `readme_generator`, Learning: `concept_explainer` |
| Workflows | [`workflows/creating_a_new_lesson.md`](workflows/creating_a_new_lesson.md) |

## Phase 2 guides & agents
- [Codex Interfaces Guide](docs/codex_interfaces_guide.md) – compare web, IDE, and CLI usage and learn when to switch surfaces.
- [Agent System Guide](docs/agent_system_guide.md) – understand how `.agent.md` files work and how to create your own.
- [Getting Started Walkthrough](docs/getting_started_walkthrough.md) – run three starter exercises across web, IDE, and CLI.
- Agent quick reference (see `agents/` for details):
  - `repo_teacher.agent.md` – turns repo knowledge into lessons and cheat sheets.
  - `workflow_architect.agent.md` – designs automation workflows with interface recommendations.
  - `prompt_librarian.agent.md` – curates and improves prompt templates.
  - `codex_interface_advisor.agent.md` – selects the best interface and troubleshoots setup issues.

## Phase 2 documentation
The Phase 2 agent system and interface guide will live in [`docs/project_overview.md#phase-2-agent-system`](docs/project_overview.md#phase-2-agent-system). All future links in the repo will point there once Phase 2 ships.

---
Need help deciding what to add next? Check the roadmap at the end of `docs/project_overview.md` for the upcoming phases.
