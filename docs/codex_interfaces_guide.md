# ChatGPT Codex Interfaces Guide

## 1. Overview
ChatGPT Codex is the orchestration layer that lets me pair program, document, and automate through natural language. The same Codex brain is available through three surfaces—web, IDE, and CLI—each optimized for different types of work. The sections below explain when to use each path, how to stay within context limits, and how to move seamlessly between them.

### Ways to use Codex
- **Web interface** – conversational, high-bandwidth brainstorming and planning. Great for synthesizing docs, drafting prompts, or exploring research.
- **IDE integration** – in-editor code edits, inline completions, and file-aware reasoning. Best for refactors, unit tests, and review loops.
- **Command Line Interface (CLI)** – automation, scripting, and batch operations from terminal workflows, especially inside WSL.

### When to use which interface
- Choose **web** for open-ended ideation, content creation, or when you need to reason over large instructions but not necessarily entire repos.
- Choose **IDE** when the task requires precise file edits, context from multiple buffers, or when you want Codex to follow along while coding.
- Choose **CLI** for reproducible runs, scripts, and automation tasks where prompts are part of shell pipelines or used in CI-like loops.

## 2. Web Interface
### Capabilities & strengths
- Handles long-form discussions with markdown rendering and quick copy/paste.
- Fast for brainstorming, planning, requirements gathering, and documentation synthesis.
- Keeps a visible conversation history that you can branch or export.

### Limitations & constraints
- Reduced ability to inspect entire repos; relies on pasted snippets or linked context.
- Browser session length limits; context can get truncated after extended back-and-forth.
- Less suited for precise code edits unless you paste focused sections.

### Best practices
- Start each session with a **mini brief** (context, goal, constraints) and include file paths.
- Chunk large tasks into labeled sections (`Step 1`, `Step 2`) so Codex can reference them later.
- Pin essential instructions (like coding style) by repeating them every few turns.

### Referencing files/code
- Paste only the minimal diff or excerpt needed.
- Provide repo-relative paths (`prompts/review/structured_review.md`) so you can locate files quickly afterward.
- When referencing long documents, summarize key points first, then optionally paste the full text in a collapsible code block.

### Managing context length
- After ~20 turns, summarize the conversation and start a new thread with that summary to avoid context collapse.
- Use numbered recap bullets after each major response to keep Codex aligned.

### Prompting tips
- Explicitly request structure (“Provide a table,” “Return numbered steps”).
- Ask Codex to reflect on assumptions before executing (“List questions before drafting”).
- Use “Act as `<agent>`” phrasing to align with the agent system.

### Example workflows
- Drafting architecture notes from `references/architecture/` and saving outputs to `docs/`.
- Designing a new prompt template by iterating on examples stored under `prompts/templates/`.
- Running a live QA session on workflow patterns using summaries from `docs/workflow_patterns.md`.

## 3. IDE Integration
### Setup & configuration
- Install the ChatGPT or Codex extension in VS Code (primary environment) and authenticate via API key or account sign-in.
- Enable access to workspace files so the extension can read buffer contents you share.

### Available features
- Inline code completions and refactors.
- Side-panel chat that understands the currently open files.
- Commands to insert responses directly into files or apply patches.

### Inline suggestions workflow
1. Highlight a block of code.
2. Invoke Codex (keyboard shortcut varies by extension, e.g., `Ctrl+Shift+I`).
3. Describe the desired change (“Add pytest fixture for this class”).
4. Review the inline diff before accepting.

### Chat features
- Use the chat panel to have context-aware discussions referencing files (`@file` in some extensions).
- Pin prompts or agents by saving them as snippets for quick reuse.

### Context management
- Keep only the relevant files open to limit noise.
- Use breadcrumbs (“Currently editing `src/foo.py`; need tests in `tests/test_foo.py`”) so Codex knows scope.

### Best practices
- Commit or stash before large Codex edits for easy diff review.
- When debugging, alternate between conversation and inline actions so Codex sees updated code.
- Label each Codex request in comments (e.g., `# Codex TODO`) to remember what was generated.

### Keyboard shortcuts
- VS Code chat: `Ctrl+Alt+Enter` (Windows) to send selection to Codex (verify per extension).
- Inline completion accept: `Tab` or `Ctrl+Enter` depending on extension.
- Use custom keybindings to open agent prompts quickly (e.g., snippet hotkeys).

### Example workflows
- Running the **Workflow Architect Agent** to refactor a script while Codex edits the files directly.
- Using the **Prompt Librarian Agent** to review prompts stored under `prompts/` and apply fixes inline.
- Pairing with the **Repository Teacher Agent** to generate a new lesson in `lessons/git/` without leaving VS Code.

## 4. Command Line Interface (CLI)
### Installation & setup
- Install Codex CLI via pip (`pip install codex-cli`) inside WSL (Ubuntu) and authenticate using an API token saved in `.env.local` (ignored by git).
- Create shell aliases (`alias codex="codex-cli"`) for faster commands.

### Core commands & syntax
- `codex chat -p prompts/review/structured_review.md` – start a chat using a prompt file.
- `codex run --agent agents/workflow_architect.agent.md --input context.md` – execute an agent with supplied context.
- `codex apply --file target.py --instruction "Add logging"` – request inline edits.

### Scripting & automation
- Combine Codex with shell scripts (`scripts/*.sh`) to preprocess data before sending to Codex.
- Use here-documents to feed multi-line prompts (`codex chat <<'PROMPT' ...`).
- Schedule recurring jobs (cron/Task Scheduler) that call Codex for daily summaries.

### Piping & integration
- Pipe git diffs directly: `git diff | codex chat -p prompts/review/diff_annotation.md`.
- Integrate with `fzf` to select prompt files interactively before passing to Codex.

### Configuration options
- `.codexrc` (if supported) for default agent, temperature, and output style.
- Environment variables for API keys and default interface (web fallback).

### Best practices
- Keep prompt files under version control and reference them by path instead of inline text.
- Log CLI sessions to `references/session_logs/` for future learning.
- Dry run with `--preview` (if available) before applying large code changes.

### Example workflows
- Running automated doc generation by combining `scripts/export_outline.sh` with the **Repository Teacher Agent** via CLI.
- Triggering the **Codex Interface Advisor Agent** to suggest the best surface for an upcoming task list.
- Batch-updating prompt descriptions using the **Prompt Librarian Agent** in CLI mode.

## 5. Choosing the Right Interface
### Decision matrix
| Task type | Best interface | Rationale |
| --- | --- | --- |
| Brainstorming, planning, writing docs | Web | Long-form dialogue, easy copy/paste. |
| Code edits, refactors, test writing | IDE | Direct access to files, inline diffs. |
| Automation scripts, batch jobs, CI hooks | CLI | Scriptable, integrates with shell tools. |
| Mixed research + implementation | Web → IDE | Start broad, then apply changes in editor. |
| Workflow documentation | IDE or Web | Use whichever holds context best; finalize in repo files. |

### Multi-interface workflows
1. Draft outline in the web UI.
2. Move to IDE to implement code changes with inline support.
3. Finish by running CLI commands to validate and commit.

### Seamless switching
- Maintain short summaries when switching surfaces (“Summary of web session…” saved under `references/notes/`).
- Use consistent agent names so Codex picks up instructions no matter the interface.

## 6. Common Patterns Across Interfaces
### Effective prompting principles
- Provide role, context, goal, and constraints explicitly.
- Ask for reasoning before solutions when problems are ambiguous.
- Include success criteria or tests so Codex knows when it’s done.

### Context building strategies
- Reference repo files with relative paths.
- Summarize prior steps when continuing a conversation elsewhere.
- Attach tags (#git, #docs, #workflow) to anchors cross-interface.

### Iterative refinement
- Start broad, inspect results, then tighten instructions.
- Use “Critique the previous output” loops for continuous improvement.
- Keep diffs small and review after each iteration.

### Error handling & debugging
- Reproduce the issue, supply exact error logs or stack traces.
- Ask Codex to explain unknown commands or API behavior first, then propose fixes.
- When Codex gets stuck, restate the constraints or switch interfaces to reset context.

Use this guide as the central reference whenever deciding how to engage Codex for a task.
