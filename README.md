# PawPal+: Intelligent Pet Care Planning System

## Overview

PawPal+ is a smart scheduling application designed to help pet owners organize and prioritize their daily pet care responsibilities efficiently. The system intelligently plans tasks—including feeding, exercise, medication management, and grooming—by evaluating time constraints and task priorities to create optimized, actionable daily schedules. By providing structured guidance and clear task prioritization, PawPal+ enables pet owners to maintain consistent, high-quality care routines while maximizing time management.

## Key Features

**PawPal+** provides comprehensive pet care planning with:

- **Task Management** — Track all pet care activities (walks, feeding, medications, enrichment, grooming, and more)
- **Constraint Evaluation** — Considers available time, task priorities, and owner preferences
- **Optimized Scheduling** — Generates intelligent daily plans using task ranking and consistent prioritization
- **Transparent Reasoning** — Provides clear explanations for scheduling decisions
- **User-Friendly Interface** — Simple design for managing pet information and tasks

## Architecture Overview

PawPal+ uses a four-class system architecture: `Task` models individual care activities with time and frequency data, `Pet` manages each pet's profile and task list, `Owner` represents the caregiver and available time constraints, and `Scheduler` coordinates task organization and generates optimized daily plans. The Streamlit UI (`app.py`) provides an interactive frontend that communicates with the backend `pawpal_system.py` module, while `test_pawpal.py` ensures core scheduling logic remains reliable through automated testing.

## Setup Instructions

1. **Create and activate a Python virtual environment** (Python 3.10+):
   ```bash
   python -m venv .venv
   .venv\Scripts\activate  # Windows
   ```

2. **Install dependencies**:
   ```bash
   pip install -r requirements.txt
   ```

3. **Run the Streamlit web app**:
   ```bash
   streamlit run app.py
   ```
   Or run the CLI demo: `python main.py`

4. **Run the tests**:
   ```bash
   pytest test_pawpal.py -v
   ```

## Sample Interactions

**Example 1:** Owner adds a dog named "Buddy" with 4 available hours, then adds daily tasks (30-min walk, 10-min feeding, 15-min medication). The scheduler generates a plan that fits all tasks within the time window.

**Example 2:** Owner has 2 pets (dog and cat) with conflicting priorities—the scheduler prevents duplicate daily tasks for the same pet and orders tasks by duration to optimize the plan.

**Example 3:** Owner marks "afternoon walk" as completed; the system automatically creates the next occurrence based on the task's daily frequency, maintaining a rolling schedule for recurring activities.

## Design Decisions

We separated data models (`Task`, `Pet`, `Owner`) from scheduling logic (`Scheduler`) to keep validation and planning independent, making each class easier to test and maintain. Tasks validate inputs (time > 0, valid time format) at initialization to catch errors early, and the Scheduler uses duration-based sorting with consistent tie-breaking to produce deterministic, explainable plans even when tasks have equal priority.

## Testing Summary

PawPal+ uses pytest to verify core behaviors: task lifecycle management (creation, completion, recurring rollover), multi-pet scheduling without conflicts, and sorting consistency across different time durations. Tests confirmed that task duration validation works correctly, recurring tasks generate proper next-due dates, and the scheduler consistently ranks and orders tasks—revealing areas like edge cases with zero available time that required additional validation logic.

## Reflection

This project taught me that effective scheduling requires thoughtful separation of constraints (time, priority, frequency) and careful edge-case handling—small details like preventing duplicate tasks or handling time conflicts significantly impact system reliability. I learned that building robust AI-like systems isn't just about intelligent ranking; it's about clear validation rules, transparent decision-making, and comprehensive testing to handle the messy real-world scenarios pet owners face.

## Scenario

A busy pet owner needs help staying consistent with pet care. They want an assistant that can:

- Track pet care tasks (walks, feeding, meds, enrichment, grooming, etc.)
- Consider constraints (time available, priority, owner preferences)
- Produce a daily plan and explain why it chose that plan

Your job is to design the system first (UML), then implement the logic in Python, then connect it to the Streamlit UI.

## What you will build

Your final app should:

- Let a user enter basic owner + pet info
- Let a user add/edit tasks (duration + priority at minimum)
- Generate a daily schedule/plan based on constraints and priorities
- Display the plan clearly (and ideally explain the reasoning)
- Include tests for the most important scheduling behaviors

## Getting started

### Python version

Use Python 3.10 or newer.

### Setup

```bash
python -m venv .venv
source .venv/bin/activate  # Windows: .venv\Scripts\activate
pip install -r requirements.txt
```

### Run the app

```bash
streamlit run app.py
```

### Run the CLI demo

```bash
python main.py
```

### Suggested workflow

1. Read the scenario carefully and identify requirements and edge cases.
2. Draft a UML diagram (classes, attributes, methods, relationships).
3. Convert UML into Python class stubs (no logic yet).
4. Implement scheduling logic in small increments.
5. Add tests to verify key behaviors.
6. Connect your logic to the Streamlit UI in `app.py`.
7. Refine UML so it matches what you actually built.

## Smarter Scheduling

PawPal+ now creates more useful daily plans by ranking tasks by priority, fitting tasks within available time, and using consistent tie-breaking when tasks compete. The planner also gives clearer reasoning for task choices so owners can understand and adjust the schedule quickly.

## Sample Input/Output

**Sample Input**

An owner enters:
- Pet name: Buddy
- Available time: 4 hours
- Tasks:
   - 30-minute walk, priority 5
   - 10-minute feeding, priority 10
   - 15-minute medication, priority 9

**Sample Output**

The planner returns a schedule that fits the highest-priority tasks first and explains its choices:

```text
Daily Plan for Buddy
1. Feeding - 10 minutes
2. Medication - 15 minutes
3. Walk - 30 minutes

Reasoning: All three tasks fit within the available time, so the planner ordered them by priority and kept the result easy to follow.
```

## Short System Diagram

The system diagram has been moved to assets:

- [assets/system_diagram.md](assets/system_diagram.md)

## Testing PawPal+

To ensure your PawPal+ implementation works correctly:

```bash
# Run all tests
pytest test_pawpal.py -v

# Run tests with coverage
pytest test_pawpal.py --cov=. --cov-report=html
```

**What to test:**
- Owner and pet data validation
- Task creation and modification
- Schedule generation with various constraints
- Task ranking and prioritization logic
- Edge cases (no time available, conflicting priorities, empty task list)

Write tests incrementally as you implement each scheduling feature.

## Agentic Workflow In VS Code

This repo now includes Copilot customization files so you can use an agentic coding workflow directly in Chat.

- Project-wide guidance: `.github/copilot-instructions.md`
- Python file rules: `.github/instructions/pawpal-python.instructions.md`
- Custom coding agent: `.github/agents/pawpal-dev.agent.md`
- Reusable prompts:
  - `.github/prompts/pawpal-implement-feature.prompt.md`
  - `.github/prompts/pawpal-fix-bug.prompt.md`

How to use:

1. Open Copilot Chat in VS Code.
2. Select the **PawPal Dev** agent from the agent picker.
3. Ask for tasks like:
	- "Add recurring monthly medication reminders in planner"
	- "Fix duplicate-task conflict bug and add tests"
4. Or type `/` in chat and run:
	- `Implement PawPal Feature`
	- `Fix PawPal Bug`

Tip: include acceptance criteria in your prompt so the agent can implement and verify changes in one pass.

## 📸 Demo

Add a screenshot of your final Streamlit app here.

Use this embed format:

<a href="final_images/Screenshot%202026-04-01%20005115.png" target="_blank"><img src='final_images/Screenshot%202026-04-01%20005115.png' title='PawPal App 1' width='900' alt='PawPal App 1' class='center-block' /></a>
<a href="final_images/Screenshot%202026-04-01%20005304.png" target="_blank"><img src='final_images/Screenshot%202026-04-01%20005304.png' title='PawPal App 2' width='900' alt='PawPal App 2' class='center-block' /></a>
<a href="final_images/Screenshot%202026-04-01%20005326.png" target="_blank"><img src='final_images/Screenshot%202026-04-01%20005326.png' title='PawPal App 3' width='900' alt='PawPal App 3' class='center-block' /></a>
<a href="final_images/Screenshot%202026-04-01%20005354.png" target="_blank"><img src='final_images/Screenshot%202026-04-01%20005354.png' title='PawPal App 4' width='900' alt='PawPal App 4' class='center-block' /></a>
<a href="final_images/Screenshot%202026-04-01%20005412.png" target="_blank"><img src='final_images/Screenshot%202026-04-01%20005412.png' title='PawPal App 5' width='900' alt='PawPal App 5' class='center-block' /></a>
<a href="final_images/Screenshot%202026-04-01%20005614.png" target="_blank"><img src='final_images/Screenshot%202026-04-01%20005614.png' title='PawPal App 6' width='900' alt='PawPal App 6' class='center-block' /></a>
<a href="final_images/Screenshot%202026-04-01%20010246.png" target="_blank"><img src='final_images/Screenshot%202026-04-01%20010246.png' title='PawPal App 7' width='900' alt='PawPal App 7' class='center-block' /></a>
<a href="final_images/Screenshot%202026-04-01%20010913.png" target="_blank"><img src='final_images/Screenshot%202026-04-01%20010913.png' title='PawPal App 8' width='900' alt='PawPal App 8' class='center-block' /></a>

# MY Loom video link below:

https://www.loom.com/share/f059b15d8915443daca8e3540d426100
