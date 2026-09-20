# Tasks — Spec 001

- [x] T1. Project skeleton: habits/ package, tests/, pytest configured.
      (RF: —) Done when: `pytest -q` runs (0 tests) without errors.
- [x] T2. storage.py: load/save JSON; missing → empty structure;
      corrupt → own error without overwriting. (RF-9, RF-11)
      Done when: tests for the 3 scenarios pass.
- [x] T3. core.add_habit with normalization and duplicates. (RF-1, RF-2, RF-3)
      Done when: tests for create, duplicate (with upper case) and empty pass.
- [x] T4. core.mark_done idempotent with injected date. (RF-4, RF-5, RF-6)
      Done when: tests for done, repeated and missing habit pass.
- [x] T5. core.streak with every edge case. (RF-10)
      Done when: tests for streak 0, alive from yesterday, broken, 1 day and
      long pass.
- [x] T6. core.list_habits sorted + empty case. (RF-7, RF-8)
      Done when: tests for ordering and for the empty list pass.
- [x] T7. cli.py with argparse: add/done/list, messages in Spanish and exit
      codes. (RF-1..RF-8) Done when: CLI smoke tests pass.
- [x] T8. Final validation: spec checklist + short README. (All)
      Done when: every RF has an associated test and the manual demo is OK.
