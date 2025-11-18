# Agents Directory
Codex agents are reusable personas defined in `.agent.md` files. Each agent captures a mission, scope, knowledge sources, interaction instructions, and example prompts so you can summon it from the web, IDE, or CLI without rewriting context. Read [`docs/agent_system_guide.md`](../docs/agent_system_guide.md) for the philosophy, usage patterns, and extension rules.

## Available agents
| Agent | Mission | Best interfaces | Key directories |
| --- | --- | --- | --- |
| [`repo_teacher.agent.md`](repo_teacher.agent.md) | Turn repo knowledge into lessons, cheat sheets, and learning paths. | Web / IDE | `lessons/`, `cheatsheets/`, `references/` |
| [`workflow_architect.agent.md`](workflow_architect.agent.md) | Design multi-step Codex workflows with clear validation and handoffs. | IDE / CLI | `workflows/`, `docs/workflow_patterns.md`, `scripts/` |
| [`prompt_librarian.agent.md`](prompt_librarian.agent.md) | Curate, improve, and catalog prompt templates. | IDE / CLI | `prompts/`, `cheatsheets/`, `references/` |
| [`codex_interface_advisor.agent.md`](codex_interface_advisor.agent.md) | Recommend the right Codex interface and troubleshoot setups. | Web / CLI | `docs/codex_interfaces_guide.md`, `references/notes/` |

## Getting started with agents
1. Pick the agent aligned with your task (teaching, workflow design, prompt curation, or interface planning).
2. Open the `.agent.md` file and skim **Primary Role**, **Scope**, and **Interaction Model**.
3. In your chosen interface, paste those sections to initialize Codex, then follow with task-specific instructions.
4. Use the **Typical Tasks** section for ready-made prompts and log outcomes in `references/session_logs/`.

## Creating or updating agents
- Follow the template described in [`docs/agent_system_guide.md`](../docs/agent_system_guide.md) and `docs/contributing.md`.
- Add new agents under `agents/` with descriptive filenames (`<persona>.agent.md`).
- Update this README table whenever an agent is added or retired so the directory stays discoverable.
