# Hello SDD: Spec-Driven Development (SDD) course from scratch

[![Spec-Driven Development course](https://img.youtube.com/vi/5HaOxAAA5qI/maxresdefault.jpg)](https://youtube.com/live/5HaOxAAA5qI)

## [MoureDev](https://moure.dev) course on **Spec-Driven Development (SDD)**: building software with AI agents starting from an agreed specification, instead of improvising prompts.

> **Watching [the course](https://youtube.com/live/5HaOxAAA5qI) is essential to understand the content of this repository.**

It contains two things: the **templates** used in the course (`samples/`) and a **complete project** built step by step with SDD (`habits-cli/`).

```
HelloSDD/
├── samples/            # Course templates and material
│   ├── AGENTS.md       # Agent instructions template
│   ├── spec.md         # Specification template (RF-x in EARS notation)
│   ├── prompts.md      # Essential prompt for each phase of the SDD flow
│   └── sdd.excalidraw  # Course whiteboard (block-by-block script and diagrams)
└── habits-cli/         # Hands-on project developed with SDD
```

## `samples/` — templates

| File | What it is |
|---|---|
| `AGENTS.md` | Template for the agent's context file: what the project is, commands, style, rules and mandatory verification when finishing. `CLAUDE.md` can be reduced to just `@AGENTS.md`. |
| `spec.md` | Specification template: context, users, stories, numbered functional requirements (RF-x) in EARS notation, edge cases, out of scope, completion criteria and open questions. |
| `prompts.md` | Table with the essential prompt for each phase: constitution, spec, clarification, plan, tasks, implementation, validation and change. |
| `sdd.excalidraw` | Course whiteboard: the block-by-block script (what SDD is, vibe coding, types of SDD, EARS, workflow, practice…) and diagrams of how an agent works. Open it at [excalidraw.com](https://excalidraw.com). |

## `habits-cli/` — the project built with SDD

A Python CLI (standard library only) to track study habits and see your streak of consecutive days: `habits add`, `habits done` and `habits list`.

What matters is not the app, but **how it was built**. Every step of the SDD flow left its artifact in the repo:

| Step | Artifact |
|---|---|
| 1. Constitution | `docs/constitution.md` — 6 non-negotiable principles of the project |
| Agent context | `AGENTS.md` + `CLAUDE.md` |
| 2. Specification | `specs/001-habits-mvp/spec.md` — RF-1 to RF-11 in EARS notation |
| 3. Clarification | Reviewing the spec as QA: spots ambiguities and gaps before planning |
| 4. Planning | `specs/001-habits-mvp/plan.md` — modules, data model, streak algorithm, CLI contract and technical decisions |
| 5. Tasks | `specs/001-habits-mvp/tasks.md` — T1 to T8 with checkboxes and their "Done when:" |
| 6. Implementation | `habits/` (core + storage + cli) and `tests/`, one task at a time and tests first |
| 7. Validation | Walkthrough requirement by requirement, checking which test covers each one |

It also includes a reusable **skill**, `spec-generator` (`.claude/skills/spec-generator/`), which guides the requirements interview and generates the spec following the template. It is also linked for opencode in `.opencode/skill/`.

The exact prompts for each step, and how to run the app and its tests, are in the [habits-cli README](./habits-cli/README.md).

## The SDD flow in one line

Constitution → Spec → Clarification → Plan → Tasks → Implementation (one task at a time, tests first) → Validation → Change (spec first, then code).

## ![https://mouredev.com](https://raw.githubusercontent.com/mouredev/mouredev/master/mouredev_emote.png) Hi, my name is Brais Moure.

[![YouTube Channel Subscribers](https://img.shields.io/youtube/channel/subscribers/UCxPD7bsocoAMq8Dj18kmGyQ?style=social)](https://youtube.com/mouredevapps?sub_confirmation=1)
[![Discord](https://img.shields.io/discord/729672926432985098?style=social&label=Discord&logo=discord)](https://mouredev.com/discord)
![GitHub Followers](https://img.shields.io/github/followers/mouredev?style=social)
![GitHub Followers](https://img.shields.io/github/stars/mouredev?style=social)

I have been a software engineer since 2010. Since 2018 I have combined my work as a developer with creating educational and outreach content about programming and AI on different social networks as **[@mouredev](https://moure.dev)**.

If you want to join our development community and learn programming and artificial intelligence, you can find me at:

[![Pro](https://img.shields.io/badge/Cursos-mouredev.pro-FF5500?style=for-the-badge&logo=gnometerminal&logoColor=white&labelColor=101010)](https://mouredev.pro)
[![Link](https://img.shields.io/badge/Links_de_interés-moure.dev-14a1f0?style=for-the-badge&logo=Linktree&logoColor=white&labelColor=101010)](https://moure.dev)
