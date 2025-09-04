# Agent Usage Guide

This guide explains the roles of the different agents and how to use them effectively.

## The Agents

### 1. `@orchestrator` (Primary Agent)

The `@orchestrator` is your main point of contact. It's a primary agent that manages the entire workflow. You can give it a high-level goal, and it will delegate tasks to the appropriate sub-agents.

**Example:**
> `@orchestrator` Please add a square root function to the calculator and write tests for it.

### 2. `@architect` (Sub-agent)

The `@architect` is responsible for designing the software structure. The `@orchestrator` will typically call this agent to create a plan for a new feature.

### 3. `@coder` (Sub-agent)

The `@coder` writes the code based on the instructions from the `@orchestrator` or the `@architect`.

### 4. `@tester` (Sub-agent)

The `@tester` writes tests for the code.

### 5. `@reviewer` (Sub-agent)

The `@reviewer` reviews the code for quality, correctness, and best practices.

### 6. `@researcher` (Sub-agent)

The `@researcher` can be used to find information on the web.

**Example:**
> `@researcher` What is the best way to handle complex numbers in Python?

## Sample Workflow

Here's a sample workflow for adding a new feature to the calculator:

1.  **You:** `@orchestrator`, please add a feature to calculate the area of a circle.
2.  **`@orchestrator`:** Calls `@architect` to design the feature.
3.  **`@architect`:** Proposes adding a new function `circle_area(radius)` to `calculator.py`.
4.  **`@orchestrator`:** Approves the design and calls `@coder` to implement it.
5.  **`@coder`:** Adds the `circle_area` function to `calculator.py`.
6.  **`@orchestrator`:** Calls `@tester` to write tests for the new function.
7.  **`@tester`:** Creates `test_calculator.py` and adds tests for `circle_area`.
8.  **`@orchestrator`:** Calls `@reviewer` to review the new code and tests.
9.  **`@reviewer`:** Provides feedback.
10. **`@orchestrator`:** If there's feedback, it will coordinate the necessary changes. If not, it will report back to you that the task is complete.

## Communication Between Agents

A simple and effective way for agents to communicate and share information is by using files. For example, the `@architect` can write its design to a `design.md` file in the project's root directory. The `@coder` can then read this file to get the required context for implementation.

The `@orchestrator` can coordinate this process:

> `@orchestrator` please ask the `@architect` to create a design for a new feature and save it to `design.md`. Then, ask the `@coder` to implement the feature based on the design in that file.
