# Technical plan — Spec 001

## Module structure
- habits/storage.py → load/save JSON (RF-9, RF-11)
- habits/core.py    → pure logic: add, done, streak, list (RF-1..8, RF-10)
- habits/cli.py     → argparse, messages in Spanish, exit codes
- habits/__main__.py → enables `python -m habits`
- tests/            → pytest, one or more tests per RF

## Data model (habits.json)
{
  "version": 1,
  "habits": [
    { "name": "Study Python",
      "created_at": "2026-08-27",
      "completions": ["2026-08-25", "2026-08-26", "2026-08-27"] }
  ]
}
- ISO dates (YYYY-MM-DD), ascending order, no duplicates (RF-5).

## Streak algorithm (RF-10)
1. If there are no completions → 0.
2. last = last date. If last < yesterday → 0.
3. Count backwards from last while the dates are consecutive.

## Technical decisions
- argparse (stdlib) instead of typer/click → constitution principle no. 1.
- Name comparison: strip() + casefold(); the original is kept for display
  (RF-2).
- The "today" date is INJECTED into the core (parameter `today: date`), so
  streaks can be tested without mocking the clock. The CLI passes
  date.today().
- storage never writes if loading failed → impossible to clobber data (RF-11).

## CLI contract
- habits add <name> | done <name> | list
- stdout for results; stderr for errors; exit codes 0/1 as per the spec.

## Test strategy
- Unit tests of core with injected dates (streaks: empty, alive from
  yesterday, broken, 1 day, long).
- storage with pytest's tmp_path (missing, valid, corrupt).
- CLI smoke test invoking the parser.
