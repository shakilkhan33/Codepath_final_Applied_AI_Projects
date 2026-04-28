# PawPal+ System Diagram

```mermaid
flowchart LR
    H[Human user] --> UI[Streamlit UI app.py]
    H --> CLI[CLI demo main.py]

    UI --> S[pawpal_system.py\nTask, Pet, Owner, Scheduler]
    CLI --> S

    S --> V[Validation, conflict checks, recurrence handling]
    V --> O[Plan, task views, conflict summary, assistant log]

    O --> UI
    O --> CLI

    T[Pytest test_pawpal.py] --> S
    T --> V
```

At a glance:
- Main components: UI, CLI, core data models, scheduler engine, validation/conflict checks, and tests.
- Data flow: input -> processing in pawpal_system.py -> scheduled plan/report/output.
- This matches the current implementation: there is no database, retrieval layer, agent layer, or evaluator.

## Project Diagram

<a href="system_diagram.png.png" target="_blank"><img src='system_diagram.png.png' title='System Diagram' width='900' alt='System Diagram' class='center-block' /></a>
