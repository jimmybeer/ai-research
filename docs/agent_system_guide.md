# Agent System Guide

## 1. What Are Agents?
Agents in this repository are curated `.agent.md` briefs that encode a persona, mission, guardrails, and interface-specific instructions for ChatGPT Codex. Unlike raw prompts, agents bundle:
- **Role & scope** – what problem space they own and when to defer.
- **Interaction models** – how to invoke them from web, IDE, or CLI.
- **Knowledge sources** – which repo files or references they should read before acting.
- **Quality bars** – output structure, tone, and success criteria.

By using agents, I can reuse repeatable behaviors (reviews, documentation, workflow design) without rewriting context each time. Agents sit above prompts: a prompt is a single instruction; an agent is an operating manual with example prompts embedded.

### Agent file structure (`*.agent.md`)
Each agent file follows the template in `docs/contributing.md` and includes sections for primary role, scope, knowledge sources, interaction model, style, constraints, capabilities, example prompts, dependencies, and version history. Store agents in `agents/` with descriptive names (`workflow_architect.agent.md`).

## 2. How to Use Agents
### 2.1 Web Interface
1. Open ChatGPT in the browser and start a new conversation.
2. Paste the agent’s **Primary Role**, **Scope**, and **Constraints** sections to set context.
3. Provide any linked repo files (copy/paste or summarize) the agent expects.
4. Use one of the **Example Prompts** to kick off the session.
5. Every ~10 exchanges, remind Codex which agent is active and restate the target outcome.

**Example starter**
> “Act as the Workflow Architect Agent from `agents/workflow_architect.agent.md`. You have access to `docs/workflow_patterns.md` and `scripts/README.md`. Help me design an automation for reviewing PRs nightly.”

**Managing long conversations**
- Summarize progress in numbered lists.
- Clip outputs to relevant sections of the repo immediately (e.g., save to `workflows/`).

### 2.2 IDE Integration
1. Open the agent file in VS Code.
2. Highlight the **Primary Role**, **Scope**, and **Interaction Model** text and send it to the Codex chat panel (many extensions support `Cmd/Ctrl+Shift+I`).
3. Provide the target files (use the extension’s “Add file to chat” feature or paste excerpts) and state the task.
4. Use inline suggestions for edits while referencing the agent’s constraints.

**Example workflow**
- Load the Prompt Librarian Agent, open `prompts/testing/test_scaffold.md`, and ask the chat panel: “Using the Prompt Librarian Agent, review this file for clarity and add missing guardrails. Suggest inline edits.”

**Multi-file context**
- Use split editors to show `references/` or `docs/` while conversing so Codex sees the broader picture.

### 2.3 CLI Usage
1. Reference the agent file in your command: `codex chat -p agents/repo_teacher.agent.md`.
2. Pass additional context via `--context` flags or by piping files: `codex chat -p agents/workflow_architect.agent.md < context.md`.
3. For scripted runs, wrap commands in shell functions stored under `scripts/`.

**Example CLI flow**
```bash
codex chat -p agents/codex_interface_advisor.agent.md <<'PROMPT'
Task: choose interfaces for upcoming sprint activities listed in references/sprint_plan.md
PROMPT
```

**Combining with other tools**
- Pipe git diffs, log outputs, or JSON specs into Codex while the agent instructions remain constant.

## 3. Available Agents (Phase 2)
| Agent | Primary mission | Ideal interface | Key directories |
| --- | --- | --- | --- |
| Repository Teacher | Convert repo knowledge into lessons, cheat sheets, and learning paths. | Web or IDE | `lessons/`, `cheatsheets/`, `references/` |
| Workflow Architect | Design, document, and refine multi-step automations. | IDE or CLI | `workflows/`, `docs/workflow_patterns.md`, `scripts/` |
| Prompt Librarian | Curate, improve, and index prompt templates. | IDE or CLI | `prompts/`, `references/`, `cheatsheets/` |
| Codex Interface Advisor | Recommend interfaces, troubleshoot setups, and plan multi-surface flows. | Web or CLI | `docs/codex_interfaces_guide.md`, `references/notes/` |

**Choosing an agent**
- Pick based on the end artifact (lesson, workflow, prompt, interface plan).
- Combine agents by running them sequentially: e.g., Codex Interface Advisor suggests surfaces, then Workflow Architect designs the process.

## 4. Creating Your Own Agents
1. Copy `agents/template.agent.md` (create one if needed) or reuse an existing file as a base.
2. Define a specific mission and clear boundaries.
3. Identify knowledge sources—link to directories/files.
4. Fill out interaction instructions for web, IDE, CLI.
5. Add at least 7 example prompts that span difficulty levels.
6. State success criteria and red flags.
7. Commit with `feat(agent): add <agent_name>` and update `agents/README.md`.

**Best practices**
- Keep agents single-purpose; if the scope grows, split into specialized agents.
- Use consistent tone and formatting so Codex can parse sections reliably.
- Version entries in the `Version History` to track evolution.

**Testing & refinement**
- Run the agent in all three interfaces and note gaps.
- Capture improvements in `references/agent_feedback.md`.
- Update `Example Prompts` whenever you find a better phrasing.

## 5. Modifying Existing Agents
### When to customize
- The scope drifts (e.g., Workflow Architect needs a new stage for deployment).
- New repo directories or tools appear that the agent should reference.
- You discover a better prompting style or additional constraints.

### How to modify
1. Create a branch (`feat/agent-update-workflow-architect`).
2. Edit the `.agent.md` file, update `Version History`, and adjust `agents/README.md` if scope changed.
3. Test the agent in the relevant interface to confirm behavior.
4. Document the change in PR description (including screenshots or chat logs). 

### Forking vs. modifying
- **Fork** when the new behavior is fundamentally different (e.g., a QA-focused version of the Repository Teacher). Save under a new filename.
- **Modify** when you only need refinements (extra capabilities, better prompts, or updated knowledge sources).

Keep this guide alongside the agents so every change remains intentional and traceable.
