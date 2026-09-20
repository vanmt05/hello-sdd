# Project: `habits-cli`

A Python terminal app to track study habits and see your streak of consecutive days.

## Commands
```
habits add "study python"     → creates a habit
habits done "study python"    → marks the habit as done TODAY
habits list                   → lists habits with their current streak
```

## Project structure

```
habits-cli/
├── AGENTS.md
├── CLAUDE.md                      # one line: @AGENTS.md
├── docs/
│   └── constitution.md
├── specs/
│   └── 001-habits-mvp/
│       ├── spec.md
│       ├── plan.md
│       └── tasks.md
├── habits/
│   ├── __init__.py
│   ├── __main__.py
│   ├── cli.py
│   ├── core.py
│   └── storage.py
└── tests/
    ├── test_cli.py
    ├── test_core.py
    └── test_storage.py
```

## Usage

```bash
python -m habits add "Study Python"   # creates the habit
python -m habits done "Study Python"  # marks it as done TODAY (idempotent)
python -m habits list                 # lists by streak descending
```

Data is stored in a single readable JSON file inside the project itself:
`habits.json`, at the root of the repository (ignored by git).
Exit codes: `0` if everything went well, `1` on any error (empty name, duplicate,
missing habit or corrupt file). A corrupt file is never overwritten.

## Development

```bash
python -m venv .venv && .venv/bin/pip install pytest
.venv/bin/python -m pytest -q
```

## SDD prompts

### 1. Setup, constitution and AGENTS.md

**Constitution:**

```text
We are going to create the constitution of a new project: a Python CLI to
track study habits and compute streaks. It is an educational project that
must be maintainable by a junior developer.

Propose a docs/constitution.md with 6 non-negotiable principles, short and
verifiable, covering: simplicity of the stack, relationship between spec and
code, separation of logic and interface, test policy, data persistence, and
the language of the code and the messages. Maximum 15 lines. Wait for my
approval.
```

*Generates [/docs/constitution.md](./docs/constitution.md)*

*We write the [AGENTS.md](./AGENTS.md) and the [CLAUDE.md](./CLAUDE.md)*

**Specification:**

```text
Do NOT write code at any point. We are going to write the specification of the
first feature of habits-cli. Read docs/constitution.md.

Initial idea: a CLI with three commands: create a habit, mark it as done
today, and list the habits with their streak of consecutive days.

Your job:
1. Ask me questions ONE at a time to remove ambiguities (edge cases, behavior
   on errors, what is out of scope for the MVP). Maximum 6 questions.
2. With my answers, generate specs/001-habits-mvp/spec.md with this structure:
   context and goal, users, user stories, numbered functional requirements
   (RF-x) with acceptance criteria in EARS notation, non-functional
   requirements, edge cases, out of scope, completion criteria and open
   questions marked as [NEEDS CLARIFICATION].
3. The WHAT and the WHY. No stack, architecture or file names: that goes in
   the plan.
```

*Generates [specs/001-habits-mvp/spec.md](./specs/001-habits-mvp/spec.md)*

**Clarification:**

```text
Review specs/001-habits-mvp/spec.md as if you were a very professional QA.
List: (1) remaining ambiguities, (2) contradictions between requirements,
(3) edge cases not covered, (4) conflicts with docs/constitution.md.
Do not propose solutions yet: only detect. Format: numbered list.
```

**Planning:**

```text
Read docs/constitution.md and specs/001-habits-mvp/spec.md. Do NOT write code.
Generate specs/001-habits-mvp/plan.md with: module structure, JSON data model
with an example, streak computation algorithm in pseudocode, CLI contract
(commands, outputs, exit codes), justified technical decisions (and their
discarded alternative), and test strategy. Everything must respect the
constitution and cover every RF. State which RF each part covers.
```

*Generates [specs/001-habits-mvp/plan.md](./specs/001-habits-mvp/plan.md)*

**Tasks:**

```text
From spec.md and plan.md, generate specs/001-habits-mvp/tasks.md:
small tasks (max. 20-30 min each), in dependency order, each one with the RFs
it covers and a verifiable "Done when:" line. Use checkboxes.
```

*Generates [specs/001-habits-mvp/tasks.md](./specs/001-habits-mvp/tasks.md)*

**Implementation:**

```text
Implement ONLY task T2 of specs/001-habits-mvp/tasks.md, following plan.md
and the constitution. Write the tests first, then the code.
Run pytest -q and show me the result. When finished: mark T2 in tasks.md,
state which RF it covers and STOP. Do not start T3.
```

*Generates the code implementation inside /habits*

**Validation**

```text
Walk through specs/001-habits-mvp/spec.md requirement by requirement (RF-1 to
RF-11). For each one state: which test covers it, and the result of running it.
If any RF is not covered or fails, say so clearly. Then check the completion
criteria and give me a verdict: is the spec fulfilled?
```

**Next steps**

```text
New requirement for habits-cli: mark yesterday as done with
`habits done <name> --ayer`. Do NOT touch code. First: update
specs/001-habits-mvp/spec.md (new RF with EARS + edge cases: what if
yesterday was already marked? does it affect the streak?) and show me the
diff of the spec.
```
