# Lesson: Using Codex CLI Basics

**Difficulty:** Intermediate  
**Estimated Time:** 45 minutes  
**Prerequisites:**
- Access to WSL with Python 3.10+ and Git installed
- Codex CLI installed (`pip install codex-cli`) and authenticated
- Familiarity with terminal navigation and basic git commands

**Learning Objectives:** After completing this lesson you will be able to:
1. Configure and verify the Codex CLI environment inside WSL.
2. Run prompts and agents from the CLI using repo files as context.
3. Pipe command output (e.g., git diff) directly into Codex for review tasks.
4. Capture CLI conversations and logs back into the repository.
5. Automate repeatable habits with scripts and aliases.

**Related Resources:** [`docs/codex_interfaces_guide.md`](../docs/codex_interfaces_guide.md), [`docs/getting_started_walkthrough.md`](../docs/getting_started_walkthrough.md), [`cheatsheets/codex_cli_commands.md`](../cheatsheets/codex_cli_commands.md), [`agents/workflow_architect.agent.md`](../agents/workflow_architect.agent.md).

---

## 1. Introduction
The Codex CLI is your automation workhorse: it lets you combine prompts, agents, and shell commands without leaving the terminal. Mastering the CLI means you can batch-run reviews, log outcomes, and integrate Codex into scripts, CI, or cron jobs. After this lesson you will:
- Launch Codex interactions from prompt files or agents with reproducible commands.
- Feed real-time context (diffs, logs) into Codex for analysis.
- Save transcripts and follow-up tasks into the repo for later review.

**Use cases** include nightly code review sweeps, automated documentation drafting, rapid testing feedback loops, and pairing Codex with git hooks for pre-commit guidance.

---

## 2. Core Content
### 2.1 Verify installation
1. Activate your Python virtual environment if needed: `source .venv/bin/activate`.
2. Run `codex --version`. Expect output similar to `codex-cli 0.4.1`.
3. If authentication is required, set `CODEX_API_KEY` in `.env.local` and export it in your shell profile.

> **Pitfall:** forgetting to export environment variables in WSL results in `401 Unauthorized`. Add `export CODEX_API_KEY=...` to `~/.bashrc`.

### 2.2 Running a prompt file
1. Create or locate a prompt file, e.g., `prompts/review/quick_checklist.md`.
2. Run:
   ```bash
   codex chat -p prompts/review/quick_checklist.md -o references/session_logs/$(date +%F)-review.log
   ```
3. The `-o` flag stores the transcript; open it later to capture learnings.

**Pro tip:** keep prompts organized so you can select them with `fzf`: `codex chat -p $(rg --files prompts | fzf)`.

### 2.3 Invoking an agent with context
1. Use the Workflow Architect Agent to draft an automation plan:
   ```bash
   codex chat -p agents/workflow_architect.agent.md --context references/planning/weekly_plan.md
   ```
2. Codex reads the agent instructions plus the `--context` file to tailor responses.
3. Capture output to `workflows/drafts/<name>.md` for refinement.

**Pitfall:** Large context files can exceed limits. Trim them with `head -n 200` before piping.

### 2.4 Piping command output
1. Run a git diff and send it to Codex with the Prompt Librarian Agent:
   ```bash
   git diff HEAD~1 | codex chat -p agents/prompt_librarian.agent.md --label "Prompt audit"
   ```
2. Codex will analyze the diff (e.g., prompt changes) and suggest improvements.
3. Save recommended actions into `references/session_logs/`.

### 2.5 Automating with scripts
- Create a helper script (`scripts/run_codex_review.sh`):
  ```bash
  #!/usr/bin/env bash
  set -euo pipefail
  git diff $1 | codex chat -p prompts/code/code_review_checklist.md --label "CLI Review"
  ```
- Make it executable (`chmod +x scripts/run_codex_review.sh`).
- Use `./scripts/run_codex_review.sh HEAD` to review staged changes automatically.

**Optimization:** Add shell aliases in `.bashrc`:
```bash
alias codex-review='codex chat -p prompts/code/code_review_checklist.md'
alias codex-agent='codex chat -p agents/repo_teacher.agent.md'
```

### 2.6 Logging outcomes
- Redirect output to structured files:
  ```bash
  codex chat -p agents/repo_teacher.agent.md <<'PROMPT' | tee references/session_logs/$(date +%F)-lesson.log
  Goal: convert today's workflow notes into a lesson outline
  PROMPT
  ```
- Tag logs with metadata at the top (`Tags: cli, lesson`) for searchability.

---

## 3. Hands-On Exercises
1. **Warm-up (5 min):** Run `codex --help` and list three commands you did not know. Save notes to `references/session_logs/<date>-warmup.md`.
2. **Prompt replay (10 min):** Use `codex chat -p prompts/code/code_review_checklist.md` on a small diff. Paste Codex feedback into a PR or issue body.
3. **Agent-assisted planning (15 min):** Provide `references/notes/<topic>.md` to `agents/repo_teacher.agent.md` and generate a lesson outline. Store the result under `lessons/drafts/`.
4. **Automation challenge (15 min):** Write a simple Bash script that pipes `pytest` output into Codex for triage. Test it and document the workflow in `workflows/testing/`.

*Hints:* If the CLI reports missing files, check paths relative to repo root. For large outputs, pipe through `head -n 200`.

---

## 4. Troubleshooting
| Issue | Cause | Fix |
| --- | --- | --- |
| `codex: command not found` | Virtualenv not active or PATH misconfigured | Reinstall `codex-cli` inside `.venv` and ensure `.venv/bin` is on PATH. |
| `401 Unauthorized` | Missing/expired API key | Export `CODEX_API_KEY` and re-run `codex auth login` if required. |
| CLI hangs on large input | Exceeding token limits | Summarize input or use smaller diffs (`git diff --stat`). |
| Output not saved | Missing `-o` or `tee` | Re-run command with explicit redirection to a log file. |

For advanced debugging, run with `--verbose` to inspect payloads, or capture HTTP logs using `COD__LOG_LEVEL=debug` (if supported by CLI).

---

## 5. Summary & Next Steps
**Key takeaways:**
- The Codex CLI ties prompts, agents, and scripts into reproducible commands.
- Context can come from files, pipes, or inline here-docs.
- Logging conversations turns ad-hoc chats into reusable knowledge.

**Apply what you learned:**
- Add aliases or scripts for your most common Codex actions.
- Use the Workflow Architect Agent to design a CLI-first automation loop.
- Capture every CLI session in `references/session_logs/` for future lessons.

**Where to go next:**
- Try the [Creating a New Lesson workflow](../workflows/creating_a_new_lesson.md).
- Explore the Repository Teacher Agent to convert CLI outputs into lessons.
- Review [`cheatsheets/codex_cli_commands.md`](../cheatsheets/codex_cli_commands.md) for deeper command coverage.

---

## 6. Additional Resources
- Internal: `docs/codex_interfaces_guide.md`, `docs/agent_system_guide.md`, `docs/workflow_patterns.md`.
- External: [OpenAI API docs](https://platform.openai.com/docs), [VS Code Remote Development with WSL](https://code.visualstudio.com/docs/remote/wsl), [GNU Bash manual](https://www.gnu.org/software/bash/manual/).
- Community: Share CLI tips in `references/community/notes.md` to build a personal FAQ.
