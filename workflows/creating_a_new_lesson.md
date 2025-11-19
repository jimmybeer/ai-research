# Workflow: Creating a New Lesson

## Overview
- **Purpose:** Produce a polished lesson (like `lessons/using_codex_cli_basics.md`) from raw notes or workflows.
- **When to use:** Anytime you want to document a repeatable learning path or capture new Codex techniques.
- **Prerequisites:**
  - Completed research notes or workflow outputs in `references/`.
  - Familiarity with `docs/contributing.md` and lesson templates.
  - Codex web, IDE, and CLI interfaces configured.
- **Estimated time:** 60–90 minutes.
- **Deliverable:** Markdown lesson file under `lessons/<topic>/` or root, including objectives, exercises, and references.

---

## Step-by-Step Workflow

### Step 1. Gather Source Material
- **Interface:** Web or CLI
- **Agent:** Codex Interface Advisor (optional)
- **Goal:** Identify what content exists and what interface mix is ideal.
- **Instructions:**
  1. Run the Codex Interface Advisor Agent with your task list (`references/notes/lesson_ideas.md`).
  2. Confirm which surfaces (web for ideation, IDE for editing, CLI for logging) fit your situation.
- **Expected Output:** Short plan outlining interfaces and resources.
- **Quality Check:** Ensure source files are listed; if not, locate additional references.
- **Troubleshooting:** If unsure which interface to start with, use the decision matrix in `docs/codex_interfaces_guide.md`.

### Step 2. Outline the Lesson
- **Interface:** Web
- **Agent:** Repository Teacher
- **Goal:** Build the lesson skeleton (objectives, sections, exercises).
- **Instructions:**
  1. Paste relevant references (workflow notes, prompts) into ChatGPT web.
  2. Invoke the Repository Teacher Agent and request a structured outline.
  3. Ask for bullet objectives, prerequisites, and section headings.
- **Expected Output:** Lesson outline saved to `lessons/drafts/<topic>_outline.md`.
- **Quality Check:** Outline includes introduction, core content, exercises, troubleshooting, and resources.
- **Troubleshooting:** If output is generic, feed more context or specify target audience/difficulty.

### Step 3. Draft Core Content
- **Interface:** IDE (VS Code)
- **Agent:** Repository Teacher (IDE chat)
- **Goal:** Flesh out sections with explanations, commands, and pitfalls.
- **Instructions:**
  1. Open the outline in VS Code.
  2. Send the outline + section instructions to IDE chat with the Repository Teacher Agent context.
  3. Apply Codex suggestions inline, editing for accuracy.
- **Expected Output:** Draft lesson file with completed sections.
- **Quality Check:** Are instructions actionable? Do sections flow logically? Add manual notes where needed.
- **Troubleshooting:** If Codex loses context, re-send the Primary Role & Scope from the agent file.

### Step 4. Create Exercises
- **Interface:** Web or IDE
- **Agent:** Repository Teacher
- **Goal:** Add hands-on exercises with solutions/hints.
- **Instructions:**
  1. Ask Codex for 3–4 exercises that scale in difficulty.
  2. Provide expected outcome formats (commands, files to edit).
- **Expected Output:** Exercise section added to the lesson.
- **Quality Check:** Exercises reference actual repo paths and encourage logging results.
- **Troubleshooting:** If exercises are too generic, supply more scenario details.

### Step 5. Add Code & Workflow Examples
- **Interface:** IDE + CLI
- **Agent:** Workflow Architect (optional)
- **Goal:** Ensure technical accuracy and include runnable commands or diagrams.
- **Instructions:**
  1. Use Workflow Architect Agent to verify steps align with `docs/workflow_patterns.md`.
  2. Run sample commands via CLI and paste real outputs (sanitized) into the lesson.
- **Expected Output:** Code blocks, ASCII diagrams, or command snippets integrated into appropriate sections.
- **Quality Check:** Commands reflect actual repo state; code compiles or commands run successfully.
- **Troubleshooting:** If discrepancies arise, re-run commands and update instructions accordingly.

### Step 6. Review & Refine
- **Interface:** All (web for narrative, IDE for edits, CLI for linting)
- **Agents:** Prompt Librarian (for clarity), Repository Teacher (for completeness)
- **Goal:** Polish the lesson for publication.
- **Instructions:**
  1. Run the Prompt Librarian Agent on the lesson file to catch tone or structure issues.
  2. Use `markdownlint` or similar tools for formatting.
  3. Have Codex summarize key takeaways to ensure the lesson matches objectives.
- **Expected Output:** Final draft ready to commit.
- **Quality Check:** All sections filled, links verified, no placeholder text remains.
- **Troubleshooting:** If formatting issues persist, use CLI to run `markdownlint` (if configured) or manually inspect headings.

### Step 7. Commit & Share
- **Interface:** CLI
- **Agent:** None (optional use of Codex for commit message suggestions)
- **Goal:** Add the lesson to version control with proper context.
- **Instructions:**
  1. Move the file to `lessons/<topic>.md` if still under drafts.
  2. Update `lessons/README.md` to include the new entry.
  3. Run `git status`, review changes, then `git commit -m "feat(lesson): add <topic> lesson"`.
  4. Push and open a PR (even for personal review) referencing this workflow.
- **Expected Output:** Committed lesson and updated indexes.
- **Quality Check:** PR description includes objectives, screenshots/logs, and agent references.
- **Troubleshooting:** If CI fails or linting errors occur, revisit Step 6.

---

## Workflow Diagram
```
[Notes] -> (Step 1: Interface Advisor) -> Plan
Plan -> (Step 2: Repo Teacher) -> Outline
Outline -> (Step 3/4: Repo Teacher) -> Draft + Exercises
Draft -> (Step 5: Workflow Architect + CLI) -> Enriched Content
Enriched Content -> (Step 6: Prompt Librarian) -> Polished Lesson
Polished Lesson -> (Step 7: CLI) -> Commit & Share
```

---

## Example Walkthrough
**Scenario:** Convert `references/git/notes.md` into a lesson on Codex-powered git workflows.
1. **Gather:** Interface Advisor suggests Web (ideation) + IDE (editing) + CLI (logging).
2. **Outline:** Repository Teacher produces sections (Intro, Preparation, Workflow Steps, Exercises).
3. **Draft:** IDE chat fills in details; CLI commands like `codex chat -p prompts/code/code_review_checklist.md` are tested live.
4. **Exercises:** Three hands-on tasks referencing `git diff`, `codex chat`, and `references/session_logs/`.
5. **Code Examples:** Workflow Architect ensures steps align with `docs/workflow_patterns.md`.
6. **Review:** Prompt Librarian catches missing guardrails; adjustments made.
7. **Commit:** Lesson saved as `lessons/git_workflow_codex.md`, added to README, and logged in commit history.

Final output: polished lesson plus log file `references/session_logs/2025-11-18-lesson.md` documenting the process.

---

## Variations
- **Quick-start lesson:** Skip Step 5 and run Steps 2–4 once to produce a lightweight guide.
- **Multi-author collaboration:** Assign Steps 2–4 to one person and Steps 5–7 to another, using PRs for handoff.
- **Workshop mode:** Combine Steps 2–5 into a live session with Codex web, then refine offline.

**Shortcuts:** Experienced users can reuse `lessons/using_codex_cli_basics.md` as a template—duplicate the file, replace sections, and run Steps 5–7 only.

---

## Quality Checklist
- [ ] Objectives are measurable and aligned with content.
- [ ] Commands and code blocks were executed/tested.
- [ ] Exercises include solutions or hints.
- [ ] Troubleshooting section covers at least three likely issues.
- [ ] Related resources link to repo files and external references.
- [ ] Lesson is referenced in `lessons/README.md` and relevant workflows.

Avoid common issues: missing logs, outdated commands, or unlinked references. If unsure, ask the Repository Teacher Agent to audit the final file.
