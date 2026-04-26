---
description: "Use when editing Python logic, scheduler behavior, task lifecycle methods, or tests in the PawPal project. Enforces validation, deterministic planning, and test updates."
applyTo: "**/*.py"
---
# PawPal Python Editing Rules

- Keep validation close to object creation/update paths.
- Raise clear `ValueError` messages for invalid user input.
- Preserve recurrence rules for daily/weekly tasks unless a task explicitly requests behavior changes.
- Keep scheduling outputs deterministic to avoid flaky tests.
- When changing logic in `pawpal_system.py`, verify `test_pawpal.py` coverage and update tests if needed.
- Keep Streamlit UI code in `app.py` focused on rendering and interaction, not deep planning logic.
- Avoid standalone-script-only features; integrate behavior changes into scheduler methods and UI flow.
- Add lightweight logging or explicit status/error surfaces for important state changes.
