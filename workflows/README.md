# Workflows Directory
Workflows describe end-to-end processes that combine prompts, agents, scripts, and interfaces. Unlike lessons (which teach) or cheatsheets (which reference), workflows act as execution blueprints.

## When to use workflows
- You already know the basics and want a repeatable process.
- You need to coordinate multiple Codex interfaces (web/IDE/CLI).
- You want to document automation loops for future reuse or PR review.

## Available workflows
| Workflow | Purpose | Interfaces | Primary Agents |
| --- | --- | --- | --- |
| [`creating_a_new_lesson.md`](creating_a_new_lesson.md) | Turn raw notes into a polished lesson using Repository Teacher, Workflow Architect, and Codex Interface Advisor. | Web / IDE / CLI | Repository Teacher, Workflow Architect, Codex Interface Advisor |

## Workflows vs. lessons
- **Lessons** teach concepts with exercises and troubleshooting.
- **Workflows** instruct you how to execute tasks step-by-step, often referencing lessons for background.

## Creating new workflows
1. Start with the template in [`docs/workflow_patterns.md`](../docs/workflow_patterns.md).
2. Define prerequisites, steps (with interfaces and agents), diagrams, variations, and quality checklists.
3. Link to related prompts, lessons, and references.
4. Update this README table once the workflow is added.
