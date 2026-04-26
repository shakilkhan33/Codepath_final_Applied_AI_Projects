---
name: "Fix PawPal Bug"
description: "Diagnose and fix a PawPal bug, then add a regression test."
agent: "PawPal Dev"
argument-hint: "Bug report, observed behavior, expected behavior"
---
Fix this PawPal bug:

${input:Bug details}

Execution checklist:
- Reproduce or infer the issue from code/tests.
- Implement a minimal safe fix.
- Add a regression test in `test_pawpal.py`.
- Run relevant tests and summarize pass/fail.
- Note any assumptions or follow-up work.
