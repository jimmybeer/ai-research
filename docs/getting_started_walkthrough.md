# Getting Started Walkthrough
Use this guide to run three hands-on exercises that introduce the repo, Codex interfaces, and the agent system. Expect roughly 40 minutes end-to-end.

## 1. Welcome & Repository Tour
- **You will learn** how the repo is organized, how agents plug in, and how to execute tasks via web, IDE, and CLI.
- **Navigation quick hits:**
  - `README.md` – high-level usage and roadmap.
  - `docs/` – deep reference guides (project overview, interfaces, agent system, workflow patterns).
  - `agents/` – `.agent.md` personas ready for Codex.
  - `prompts/`, `lessons/`, `cheatsheets/`, `workflows/` – content libraries (populated in later phases).
- **How to use this guide:** follow the exercises sequentially. Each ends with a checkpoint to capture what you learned in the repo.

## 2. Prerequisites Check
- **Tools:**
  - VS Code with Codex/ChatGPT extension installed.
  - Access to ChatGPT web interface.
  - Codex CLI installed in WSL (`pip install codex-cli`).
- **Verification steps:**
  1. Run `codex --version` from WSL (expect a version string).
  2. Open VS Code, ensure the extension can authenticate.
  3. Log into ChatGPT web and create a fresh conversation.
- **Setup links:** keep `.env.local` for API keys (ignored by git) and refer to `docs/codex_interfaces_guide.md` for interface-specific setup notes.

## 3. Exercise 1 – Use a Prompt (Web) – *10 minutes*
1. Open `prompts/README.md` to understand structure (prompts will land in later phases; for now, use any existing template or create a simple one like `prompts/review/quick_checklist.md`).
2. Copy the prompt text into ChatGPT web.
3. Provide context (e.g., paste a short diff or describe a task).
4. Ask Codex to execute the prompt and review the answer.
5. Iterate by clarifying requirements or adding constraints (e.g., “Limit to bullet points”).
6. **Checkpoint:** note what worked (or didn’t) in `references/session_logs/<date>-web.md`.

## 4. Exercise 2 – Invoke an Agent (IDE) – *15 minutes*
1. Choose an agent from `agents/README.md` (e.g., **Prompt Librarian Agent**).
2. Open the agent file in VS Code and send the **Primary Role**, **Scope**, and **Constraints** sections to the Codex chat panel.
3. Provide a target file (e.g., `prompts/sample.md`) and request improvements.
4. Observe how responses differ compared to a plain prompt—note tone, structure, and guardrails.
5. Apply suggested edits inline (use VS Code diff view before accepting).
6. **Checkpoint:** capture insights in `references/session_logs/<date>-ide.md` and update `Version History` of the agent if you tweaked instructions.

## 5. Exercise 3 – Use CLI with Repo Resources – *10 minutes*
1. From WSL, run `codex chat -p agents/workflow_architect.agent.md -i references/sample_context.md` (replace with real file).
2. Observe CLI output; redirect to a log if helpful (`... | tee references/session_logs/<date>-cli.log`).
3. Experiment with piping `git status` or `scripts/*.sh` output into Codex.
4. **Checkpoint:** append a short summary to `references/session_logs/<date>-cli.md`, including commands used.

## 6. Capability Showcase
- **Find & use a prompt:** leverage `rg "Context" prompts/` to locate prompt files quickly; load into web or CLI.
- **Consult workflow patterns:** open `docs/workflow_patterns.md` and pick a template to follow.
- **Load an agent:** in any interface, start with “Act as the `<Agent Name>` from `agents/<file>.agent.md`.”
- **Switch interfaces mid-task:** summarize the web conversation, paste into VS Code chat, continue editing, then finish with CLI validation.
- **Add new content:** whenever you learn something, create a Markdown note under `references/` or a new prompt under `prompts/` to keep knowledge central.

## 7. Common Scenarios → Solutions
| Scenario | Recommended action |
| --- | --- |
| “I need to learn about Git workflows with Codex.” | Run the Repository Teacher Agent with `docs/workflow_patterns.md` and create a lesson in `lessons/git/`. |
| “I want to automate test reviews.” | Use Workflow Architect Agent + `prompts/testing/` to design a workflow, then document it under `workflows/testing/`. |
| “I found a great prompt online.” | Normalize it using Prompt Librarian Agent and store under `prompts/<topic>/` with metadata. |
| “I’m stuck on interface setup.” | Ask the Codex Interface Advisor Agent referencing `docs/codex_interfaces_guide.md`. |
| “I need to plan a new project.” | Combine Interface Advisor (surface selection) with Workflow Architect (process) and Repository Teacher (lessons/cheat sheets). |

## 8. Your First Contribution
1. Pick one insight from the exercises (prompt variation, workflow tweak, or lesson idea).
2. Capture it:
   - Prompt → `prompts/` with proper naming.
   - Lesson idea → `references/notes/` or `lessons/` (Phase 3 stub).
   - Workflow tweak → `workflows/` or `docs/workflow_patterns.md`.
3. Follow `docs/contributing.md` for naming, style, and git workflow.
4. Commit with `docs:` or `feat:` prefix and note the exercise in the message.

## 9. Next Steps
- Bookmark `docs/agent_system_guide.md` and `docs/codex_interfaces_guide.md` for quick reference.
- Plan a weekly cadence to add at least one artifact (prompt, note, workflow) so the repo keeps evolving.
- Queue Phase 3 tasks: seed lessons, cheat sheets, prompt packs, and workflows using the agents you just configured.
