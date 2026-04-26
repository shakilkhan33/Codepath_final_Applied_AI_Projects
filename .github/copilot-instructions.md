# PawPal Project Guidelines

## Project Scope
- This project is a Python pet-care scheduler with a Streamlit UI.
- Keep domain logic in `pawpal_system.py` and keep UI wiring in `app.py`.
- Use `main.py` for CLI/demo flows only.

## Architecture Rules
- Prefer small, testable methods and explicit validation errors (`ValueError`) for bad input.
- Preserve backward compatibility where reasonable, especially for public methods used by tests.
- Avoid moving business logic into the UI layer.
- New features must be integrated into the main application flow (`pawpal_system.py` + `app.py` where applicable), not delivered as standalone scripts only.
- Any feature that processes tasks or scheduling must change real planner behavior and/or surfaced UI outputs.

## Build And Test
- Install dependencies with `pip install -r requirements.txt`.
- Run tests with `pytest test_pawpal.py -v`.
- Run app locally with `streamlit run app.py`.
- When changing scheduling behavior, update or add tests in `test_pawpal.py`.

## Python Conventions
- Keep type hints on public functions and methods.
- Follow existing style in the repo (snake_case, dataclasses for core entities, clear docstrings on core methods).
- Prefer deterministic sorting and tie-breakers for schedule-related logic.

## Safety And Change Discipline
- Make minimal, targeted edits.
- Do not break existing Streamlit interactions in `app.py`.
- If behavior changes, explain expected impact in the PR/commit message or chat response.
- Add lightweight logging or user-visible status messages for meaningful workflow actions (plan generation, conflict detection, task completion).
- Add guardrails for unsafe/invalid states and fail with clear error messages.
- Keep setup steps reproducible so another developer can run with only README instructions.

## Agentic Reasoning Workflow
- #codebase: "Implement multi-step reasoning with observable intermediate steps — tool-calls, planning steps, or a decision-making chain."
- For non-trivial tasks, present a short execution plan before edits and include concise progress updates while working.
- If multiple implementation paths exist, state the selected path and why it was chosen before applying changes.
