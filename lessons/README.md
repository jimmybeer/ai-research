# Lessons Directory
Lessons are in-depth guides that teach Codex-driven workflows through objectives, walkthroughs, and exercises. Organize lessons by topic or interface and keep filenames descriptive (`using_codex_cli_basics.md`).

## Organization
- Place general-purpose lessons at the root of `lessons/`.
- For subject-specific series, create subfolders (`lessons/git/`, `lessons/testing/`) and use numbered filenames (`01_intro.md`).
- Each lesson should follow the structure outlined in [`docs/contributing.md`](../docs/contributing.md) and reference relevant agents or prompts.

## Difficulty progression
1. **Foundational** – getting started with interfaces, prompts, or agents.
2. **Intermediate** – combining multiple interfaces or automations (e.g., CLI + scripts).
3. **Advanced** – architectural patterns, custom agent design, or cross-project workflows.

## Lesson Index
| Title | Difficulty | Estimated Time | Summary | Related Resources |
| --- | --- | --- | --- | --- |
| [`using_codex_cli_basics.md`](using_codex_cli_basics.md) | Intermediate | 45 min | Configure Codex CLI, run prompts/agents, and log outputs. | Cheatsheet, CLI prompts, Workflow Architect |

## Contributing new lessons
1. Draft an outline with the Repository Teacher Agent.
2. Follow the lesson template (objectives, introduction, core content, exercises, troubleshooting, resources).
3. Add the file under `lessons/` (or a subfolder) and update this README table.
4. Cross-link to relevant prompts, agents, and workflows so the lesson slots into the broader knowledge base.
