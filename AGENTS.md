# Repository Guidelines

## Project Structure & Module Organization
Source modules live under `src/`, grouped into `agents/` for model wrappers, `pipelines/` for training flows, and `utils/` for shared helpers. Keep exploratory notebooks in `notebooks/` with a numeric prefix (for example, `01-baseline.ipynb`) so runs sort chronologically. Tests mirror the runtime layout inside `tests/`, and lightweight assets (sample prompts, config YAML, diagrams) belong in `assets/`.

## Build, Test, and Development Commands
- `python -m venv .venv && source .venv/bin/activate` sets up an isolated toolchain.
- `python -m pip install -r requirements.txt` installs runtime dependencies; use `requirements-dev.txt` when contributing.
- `make lint` runs `ruff` plus `black --check` across `src/` and `tests/`.
- `pytest -m "not slow"` executes the fast suite; append `-m slow` before pushing research branches that touch training code.

## Coding Style & Naming Conventions
Follow PEP 8 with 4-space indentation, and keep functions under 60 lines by pushing complex logic into helpers inside `src/utils/`. Use descriptive module names such as `reward_model.py`, and prefer `AgentConfig`/`AgentRun` style CamelCase for dataclasses. Public APIs need doctrings outlining inputs, outputs, and side effects; private helpers may use inline comments sparingly.

## Testing Guidelines
Write Pytest cases in files named `test_<module>.py` that mirror the `src/` path. Parametrize stochastic behaviors and seed RNGs (`torch.manual_seed(42)`) so experiments are reproducible. Add regression fixtures under `tests/fixtures/` instead of checking binary checkpoints.

## Commit & Pull Request Guidelines
Use Conventional Commit prefixes (`feat:`, `fix:`, `chore:`) so release tooling can generate change logs. Squash noisy WIP commits locally before pushing. Pull requests need a problem statement, a short bulleted summary of code changes, test evidence (command output or screenshot), and links to related experiments or issues. Include screenshots or table snippets when updating notebooks so reviewers can verify metrics without re-running heavy jobs. Tag at least one maintainer from the agents team for architectural changes touching `pipelines/` or model definitions.

## Data & Security Notes
Never upload raw datasets or API keys; store credentials in `.env.local` and load them through `src/config.py`. Mask user data in logs and redact conversation snippets that include emails or IDs before attaching them to issues. Use `pre-commit run secrets` prior to publishing to ensure no tokens leak.
