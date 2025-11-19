# Maintenance Guide

## 1. Regular Maintenance Tasks
### Weekly
- Capture new prompts, scripts, or lessons learned in `references/` and promote the best ones into `prompts/`, `lessons/`, or `workflows/`.
- Update `references/session_logs/` with summaries of Codex sessions.
- Spot-check directory organization: ensure new files have README entries and proper names.

### Monthly
- Review each agent (`agents/*.agent.md`) for scope drift, outdated knowledge sources, or missing example prompts.
- Validate external links in docs and references; replace dead links or add notes.
- Refresh cheatsheets with new commands or CLI flags.
- Evaluate workflows for relevance; mark deprecated flows or add TODO notes for improvements.

### Quarterly
- Conduct a full documentation review (README, `docs/`, folder READMEs) for clarity and accuracy.
- Assess agent performance: run a sample task per agent and log findings in `references/agent_feedback.md`.
- Revisit repo structure: consider new categories if content volume grows.
- Archive or prune outdated content (move to `references/archive/` with rationale).

## 2. Content Quality Standards
- **Lessons:** Must include objectives, prerequisites, introduction, numbered steps, exercises, troubleshooting, and resource links. Run through instructions once to verify commands.
- **Prompts:** Include metadata, structured prompt text, customization guide, usage example, tips, and related resources. Ensure placeholders are well-described.
- **Agents:** Cover role, scope, knowledge sources, interaction models per interface, constraints, example tasks, output expectations, dependencies, success criteria, and version history.
- **Workflows:** Provide overview, step-by-step instructions with interfaces/agents, diagrams, variations, and quality checklists.

Before committing new content, run through the relevant checklist above and confirm cross-links are accurate.

## 3. Version Control Practices
- **Branches:** Use `feat/<topic>`, `docs/<topic>`, or `chore/<topic>` for isolated work.
- **Commits:** Follow Conventional Commits (`feat:`, `docs:`, `chore:`, `refactor:`). Keep commits scoped to a logical set of changes.
- **Pull Requests:** Open PRs even for solo work to force a self-review. Include summary, testing evidence (if scripts), and references to docs/agents used.
- **Tags/Releases:** Optionally tag milestones (e.g., `v1.0` after major updates). Maintain a changelog in `references/changelog.md` if versioning becomes important.

## 4. Backup and Safety
- Store the repo in a backed-up location (GitHub private repo + local copies). For OneDrive/WSL setups, ensure OneDrive sync is active.
- Never commit API keys, `.env` files, or personal data. `.gitignore` already covers common secrets—extend it if needed.
- For recovery: clone from remote, restore from OneDrive history, or revert using git history. Document recovery steps in `references/recovery.md` if you perform one.

## 5. Growth Strategy
- **Deciding what to add:** Prioritize artifacts that you refer to repeatedly or that reduce friction (new prompts, automation scripts, lessons on emerging patterns).
- **Depth vs. breadth:** Alternate between deepening existing categories (e.g., more CLI lessons) and branching into new domains (e.g., requirements management) to avoid thin coverage.
- **Refactoring cues:** When directories exceed ~10 items, add subfolders or index tables. Consolidate similar prompts or workflows to avoid duplication.
- **Archiving:** Move obsolete content to `references/archive/` with an `ARCHIVED.md` explaining why. Keep the main directories lean and relevant.

Refer back to this guide each month so the knowledge base remains trustworthy and easy to navigate.
