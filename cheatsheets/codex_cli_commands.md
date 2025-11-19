# Codex CLI Commands Cheatsheet
**Last Updated:** 2025-11-18  
**Version:** Codex CLI 0.4.x (WSL / Linux)  
**How to use:** Skim sections by task, copy commands directly, and adapt placeholders in `[brackets]`. Pair with [`docs/codex_interfaces_guide.md`](../docs/codex_interfaces_guide.md) for deeper context.

---

## Installation & Setup
### Install CLI
**Purpose:** Install Codex CLI into a virtual environment.  
**Syntax:** `pip install codex-cli`  
**Example:**
```bash
python -m venv .venv && source .venv/bin/activate
pip install --upgrade codex-cli
```
**Notes:** Run inside WSL; repeat `pip install --upgrade` monthly.

### Configure API key
**Purpose:** Persist authentication.  
**Syntax:** `export CODEX_API_KEY="<token>"`  
**Example:** `echo 'export CODEX_API_KEY=sk-...' >> ~/.bashrc`  
**Notes:** Reload shell after editing `~/.bashrc`.

### Verify
**Purpose:** Ensure CLI is reachable.  
**Syntax:** `codex --version`  
**Example:** `codex --version` → `codex-cli 0.4.1`  
**Notes:** If not found, activate `.venv`.

---

## Basic Commands
### Chat with prompt file
**Purpose:** Run structured prompt.  
**Syntax:** `codex chat -p <file> [options]`  
**Example:** `codex chat -p prompts/code/code_review_checklist.md`  
**Notes:** Use relative paths; combine with `--label` for logging.

### Chat with inline text
**Purpose:** Send ad-hoc instructions.  
**Syntax:** `codex chat <<'PROMPT' ... PROMPT`  
**Example:**
```bash
codex chat <<'PROMPT'
Summarize docs/project_overview.md
PROMPT
```
**Notes:** Great for quick questions referencing files already on disk.

### Apply edits
**Purpose:** Request file modifications.  
**Syntax:** `codex apply --file <path> --instruction "..."`  
**Example:** `codex apply --file scripts/run_codex_review.sh --instruction "add usage block"`  
**Notes:** Review patches before committing.

---

## Working with Files
### Provide context file
**Purpose:** Feed supporting material.  
**Syntax:** `codex chat -p <agent> --context <file>`  
**Example:** `codex chat -p agents/repo_teacher.agent.md --context references/git/notes.md`  
**Notes:** Multiple contexts supported via repeated `--context` flags.

### Pipe file contents
**Purpose:** Stream large output.  
**Syntax:** `cat file | codex chat -p <prompt>`  
**Example:** `git diff | codex chat -p prompts/code/code_review_checklist.md`  
**Notes:** Pipe through `head -n 200` if hitting limits.

---

## Context Management
### Labels & logging
**Purpose:** Tag sessions.  
**Syntax:** `codex chat ... --label "<tag>" -o <log>`  
**Example:** `codex chat -p agents/workflow_architect.agent.md --label "weekly-plan" -o references/session_logs/2025-11-18-plan.log`  
**Notes:** Use ISO dates in filenames.

### Temperature control
**Purpose:** Adjust creativity.  
**Syntax:** `codex chat ... --temperature 0.2`  
**Example:** `codex chat -p prompts/documentation/readme_generator.md --temperature 0.3`  
**Notes:** Lower values for deterministic outputs.

---

## Prompt Patterns
### Select prompt interactively
**Purpose:** Choose prompt via fuzzy finder.  
**Syntax:** `codex chat -p $(rg --files prompts | fzf)`  
**Example:** `codex chat -p $(rg --files prompts/code | fzf)`  
**Notes:** Requires `rg` and `fzf`.

### Multi-stage prompting
**Purpose:** Chain prompts.  
**Syntax:** `codex chat -p <promptA> | codex chat -p <promptB>`  
**Example:** `codex chat -p prompts/documentation/readme_generator.md | codex chat -p prompts/learning/concept_explainer.md`  
**Notes:** Use only when outputs are small enough; otherwise save to file first.

---

## Output Formatting
### Markdown output
**Purpose:** Force Markdown structure.  
**Syntax:** `codex chat ... --format markdown` (if supported)  
**Example:** `codex chat -p prompts/documentation/readme_generator.md --format markdown`  
**Notes:** If flag unavailable, instruct via prompt text (“Respond in Markdown table”).

### JSON output
**Purpose:** Post-process responses.  
**Syntax:** `codex chat ... --format json`  
**Example:** `codex chat -p prompts/code/code_review_checklist.md --format json > output.json`  
**Notes:** Validate JSON before piping to tools.

---

## Scripting & Automation
### Run from script
**Purpose:** Wrap CLI usage.  
**Syntax:** `bash scripts/<script>.sh`  
**Example:**
```bash
#!/usr/bin/env bash
set -e
context=$1
codex chat -p agents/workflow_architect.agent.md --context "$context"
```
**Notes:** Store scripts under `scripts/` with execution bit.

### Schedule jobs
**Purpose:** Automate tasks.  
**Syntax:** `cron` entry or Windows Task Scheduler  
**Example:** `0 20 * * 1-5 cd ~/ai-research && ./scripts/nightly_review.sh`  
**Notes:** Redirect logs to `references/session_logs/` for auditing.

---

## Troubleshooting
| Error | Meaning | Fix |
| --- | --- | --- |
| `codex: command not found` | CLI not installed or virtualenv inactive | Activate `.venv` or reinstall CLI. |
| `HTTP 401` | Auth failure | Check `CODEX_API_KEY`, re-run `codex auth login`. |
| `context too large` | Input exceeds limit | Summarize text, pass only relevant sections. |
| `Broken pipe` | Downstream command closed early | Add `set -o pipefail` in scripts; ensure receiving command stays open. |

See [`docs/codex_interfaces_guide.md`](../docs/codex_interfaces_guide.md) for deeper debugging tips.

---

## Real-World Examples
1. **Review latest commit:**
   ```bash
   git show HEAD | codex chat -p prompts/code/code_review_checklist.md --label "commit-review"
   ```
2. **Generate README draft:**
   ```bash
   codex chat -p prompts/documentation/readme_generator.md --context references/project_notes.md > README_draft.md
   ```
3. **Design workflow plan:**
   ```bash
   codex chat -p agents/workflow_architect.agent.md --context references/planning/weekly_plan.md -o workflows/drafts/plan.md
   ```
4. **Explain concept quickly:**
   ```bash
   codex chat -p prompts/learning/concept_explainer.md <<'PROMPT'
   Topic: vector databases
   Style: ELI5 + developer tips
   PROMPT
   ```
5. **Batch script:**
   ```bash
   ./scripts/run_codex_review.sh HEAD~2 | tee references/session_logs/$(date +%F)-batch.log
   ```
6. **Prompt audit:**
   ```bash
   rg -l "TODO" prompts | xargs -I{} codex chat -p agents/prompt_librarian.agent.md --context {}
   ```
7. **Interface advice:**
   ```bash
   codex chat -p agents/codex_interface_advisor.agent.md --context references/tasks/sprint_plan.md
   ```

---

Keep this cheatsheet close while working in the terminal. Update it whenever new CLI flags or scripts enter your workflow.
