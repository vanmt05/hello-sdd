# Constitution — habits-cli

Non-negotiable principles. Every spec, plan and task must comply with them.

1. **Simplicity first**: Python 3.12+ and standard library only in the
   application. The only development dependency allowed: pytest.
2. **The spec rules**: no behavior is implemented if it is not in the active
   spec. If a decision is missing, work stops and the question is asked.
3. **Logic separated from interface**: the core does not print or read from
   the console. The CLI is a thin layer. The whole core is testable without
   the CLI.
4. **Tests as a gate**: every task ends with its tests passing. Moving
   forward with failing tests is forbidden.
5. **Local and transparent data**: persistence in a single readable JSON
   file. No databases, no network.
6. **Language**: code and identifiers in English; user-facing messages in
   Spanish and documentation in English.
