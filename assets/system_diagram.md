# PawPal+ System Diagram

```mermaid
flowchart LR
    H[Human User] --> UI[Streamlit UI app.py]
    UI --> M[Owner or Pet or Task Models]
    M --> S[Scheduler pawpal_system.py]
    S --> R[Daily Plan plus Assistant Log]
    R --> UI
    UI --> H

    S --> V[Validation and Conflict Checks]
    V --> UI

    T[Pytest test_pawpal.py] --> C[Core Scheduling Logic]
    C --> T
    H -. manual review and task edits .-> UI
```

At a glance:
- Main components: UI, model layer, scheduler engine, validator/conflict checker, and tests.
- Data flow: input -> process -> output follows user/task input -> scheduler -> plan/report shown back to the user.
- Human and testing checks: user reviews and edits results in UI; pytest verifies scheduling behavior automatically.

## Project Diagram

<a href="system_diagram.png.png" target="_blank"><img src='system_diagram.png.png' title='System Diagram' width='900' alt='System Diagram' class='center-block' /></a>
