# AGENTS.md — habits-cli

## Project
Python CLI to track study habits and compute streaks of consecutive days.
Pure core (`habits/core.py`) + CLI layer (`habits/cli.py`).
Persistence in a local JSON file (`habits/storage.py`).

## Commands
- Run: `python -m habits <command>`
- Tests: `pytest -q`

## Style
- Python 3.12+, type hints on every public function.
- Standard library only (pytest for tests only).
- Identifiers in English; user-facing messages in Spanish.

## Rules
- Read `docs/constitution.md` and the active spec in `specs/` before touching code.
- Do not add dependencies or change the JSON format without updating the spec first.
- Do not modify files inside `specs/` unless explicitly asked.

## When finishing any task
- Run `pytest -q` and confirm in your answer that everything passes.
