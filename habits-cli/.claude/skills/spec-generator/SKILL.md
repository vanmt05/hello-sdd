---
name: spec-generator
description: Use this skill when the user asks to create, write or review a specification (spec) for a feature. It guides a requirements interview and produces a spec.md following the team template.
---

# Spec generator

Turns a vague idea into an agreed specification. The spec is the contract: if
something is not here, it does not get implemented.

## Process

1. **Read the context.** `docs/constitution.md` if it exists, and the previous
   specs in `specs/` to respect conventions and not contradict what was
   already agreed.
2. **Interview the user.** Questions **ONE at a time**, maximum 6, waiting for
   an answer before the next one. Focus on edge cases, behavior on errors and
   what is out of scope. Do not propose technical solutions: if the user asks
   "how would you do it?", redirect to the WHAT.
   Prioritize questions whose answer changes what has to be built; drop the
   ones with an obvious default answer.
3. **Pick the number.** Look at `specs/` and use the next free one with three
   digits: `specs/NNN-<name-in-kebab-case>/spec.md`.
4. **Write it** using this skill's `spec-template.md`, without skipping
   sections. Acceptance criteria **always in EARS notation**, numbered as
   RF-1, RF-2, … Every requirement must be verifiable: if you cannot think of
   how to check it, it is badly written.
5. **Mark what you do not know** as `[NEEDS CLARIFICATION: specific question]`.
   Never fill a gap by inventing: a visible gap is information, a silent
   assumption is debt.
6. **Ask for explicit approval** when finished. Do not move on to the plan or
   write code until you have it.

## Rules

- The spec describes **WHAT** and **WHY**. Including stack, architecture, file
  names, data schemas, algorithms or function signatures is forbidden: that
  goes in the plan.
- **Always** include the "Out of scope" section. It is the one that keeps the
  feature from growing on its own.
- One requirement, one sentence. If you need an "and" to join two behaviors,
  they are two requirements.
- No unmeasurable adjectives: "fast", "intuitive", "robust" are not
  requirements. Write the threshold or do not write it.
- Language: the one from the project constitution. If there is none, the
  user's.

## EARS notation

Five patterns. Pick the one that fits, do not mix them:

| Pattern | Form | When |
|---|---|---|
| Ubiquitous | THE SYSTEM SHALL \<do\> | always true |
| Event-driven | WHEN \<trigger\>, THE SYSTEM SHALL \<do\> | responds to something |
| State-driven | WHILE \<state\>, THE SYSTEM SHALL \<do\> | during a condition |
| Optional | WHERE \<feature\>, THE SYSTEM SHALL \<do\> | only if it is present |
| Unwanted | IF \<condition\>, THEN THE SYSTEM SHALL \<do\> | errors and edge cases |

A well written example:

> RF-4: IF the name already exists (comparison ignoring case and outer
> spaces), THEN THE SYSTEM SHALL not create a duplicate and SHALL report the
> conflict (exit code 1).

Badly written, for contrast:

> ~~RF-4: The system must handle duplicates well and be fast.~~
> No EARS pattern, no verifiable criterion, two ideas in one sentence and an
> unmeasurable adjective.

## When reviewing an existing spec

If the user asks to review instead of create, do not rewrite: **detect and
list**, numbered, in four blocks — (1) ambiguities, (2) contradictions between
requirements, (3) edge cases not covered, (4) conflicts with the constitution.
Do not propose solutions until asked.
