# Spec 001 — habits-cli MVP

## Context and goal
Programming students drop study habits for lack of tracking. habits-cli lets
you record habits and see your streak of consecutive days from the terminal,
frictionlessly, to reinforce consistency.

## Users
Students and developers who live in the terminal. A single user per machine;
no accounts, no sync.

## User stories
- H1: As a student I want to create habits with a name so that I have the list
  of what I want to work on every day.
- H2: As a student I want to mark a habit as done today to record my
  consistency.
- H3: As a student I want to see my habits with their current streak to
  motivate me not to break it.

## Functional requirements (acceptance criteria in EARS)

### Create habit (H1)
- RF-1: WHEN the user runs `habits add <name>` with a non-empty name that does
  not exist, THE SYSTEM SHALL create the habit and confirm it with a message
  (exit code 0).
- RF-2: IF the name already exists (comparison ignoring upper/lower case and
  leading or trailing spaces), THEN THE SYSTEM SHALL not create a duplicate
  and SHALL report the conflict (exit code 1).
- RF-3: IF the name is empty or only spaces, THEN THE SYSTEM SHALL reject the
  command with an error message (exit code 1).

### Mark as done (H2)
- RF-4: WHEN the user runs `habits done <name>` and the habit exists, THE
  SYSTEM SHALL record the current date as completed and confirm it
  (exit code 0).
- RF-5: IF the habit is already completed today, THEN THE SYSTEM SHALL report
  it without duplicating the record (idempotent operation, exit code 0).
- RF-6: IF the habit does not exist, THEN THE SYSTEM SHALL show an error
  suggesting to check `habits list` (exit code 1).

### List with streaks (H3)
- RF-7: WHEN the user runs `habits list`, THE SYSTEM SHALL show every habit
  with its current streak in days, sorted by streak descending and, on ties,
  by name alphabetically (exit code 0).
- RF-8: WHILE no habit exists, THE SYSTEM SHALL answer `habits list` with a
  message inviting the user to create the first one (exit code 0).

### Cross-cutting rules
- RF-9: THE SYSTEM SHALL store all data in a single local, human-readable JSON
  file.
- RF-10: THE SYSTEM SHALL compute the streak as the number of consecutive
  completed days whose last day is today or yesterday; if the last record is
  earlier than yesterday, the streak is 0.
- RF-11: IF the data file exists but is not valid JSON, THEN THE SYSTEM SHALL
  abort with a clear message and SHALL NOT overwrite the file (exit code 1).

## Non-functional requirements
- Immediate response (<1 s) on modest machines. No network access.
- Cross-platform: macOS, Linux and Windows.
- User-facing messages in Spanish, clear and actionable.

## Edge cases already covered
- Double `done` on the same day → RF-5.
- Streak with a gap of more than one day → RF-10 (streak 0).
- Done yesterday but not yet today → RF-10 (the streak is kept).
- Missing file → an empty structure is created (part of RF-9).
- Corrupt file → RF-11.

## Out of scope (MVP)
Editing, renaming or deleting habits; marking past dates; statistics; colors;
reminders; sync; TUI interface.

## Completion criteria
- Every RF covered by at least one automated test and `pytest -q` passing.
- Manual demo of the add → done → list flow without errors.

## Open questions
- None. (The 6 initial questions were resolved during clarification.)
