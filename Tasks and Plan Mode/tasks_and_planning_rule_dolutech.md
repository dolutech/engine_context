# Tasks and Planning Rule – Dolutech Standard for AI Agents

## Objective

This rule ensures that for every prompt or request received, the AI agent operates in two structured modes: **Planning Mode** and **Execution Mode**. The agent must always generate a detailed breakdown of tasks, explain the approach, and present an execution plan for user approval before implementing any solution.

---

## Operating Modes

### 1. Planning Mode

**Whenever a new prompt or project request is received:**

- The agent must **analyze the request** and break down the solution into a list of logical, actionable tasks.
- For each task, the agent must explain:
  - **What** will be done
  - **How** it will be accomplished (tools, methods, steps)
  - **What the expected outcome** or deliverable is
- The agent must organize all tasks into a **step-by-step execution plan** (ordered list or table), including dependencies if applicable.
- The agent must present the complete execution plan to the user, asking for review, validation, or approval before proceeding.

**Example structure:**

```
## Execution Plan for [Prompt/Project Name]

1. **Task Name**
   - Description: Briefly explain what will be done.
   - Approach: Detail tools, frameworks, or techniques to be used.
   - Dependencies: [if any]
   - Expected Outcome: Describe the expected deliverable or result.

2. **Next Task**
   ...
```

- At the end, include a prompt for the user:
  - "**Please review the execution plan and indicate which tasks you approve for execution, or suggest changes as needed.**"

---

### 2. Execution Mode

- Only after explicit user approval does the agent proceed to **Execution Mode**.
- The agent executes the approved tasks step by step, documenting progress, results, decisions, and any obstacles encountered.
- If unexpected complexity or new subtasks arise, the agent must pause, return to Planning Mode, and update the plan for new approval.

---

## Task Documentation

- For each prompt or project, create or update a file in the `memory-bank` folder called `tasks_[prompt-name].md`.
- Document in this file:
  - The original user request
  - The proposed execution plan
  - User approval/comments
  - Task progress, completion notes, and final deliverables
  - Relevant links, references, or artifacts

---

## User Approval Flow

- The agent **never proceeds to execution** or delivers code, scripts, documentation, or any action without first presenting the plan and obtaining explicit user approval.
- This ensures traceability, expectation alignment, and full transparency in the workflow.

---

## Best Practices

- Always provide clear, concise, and actionable explanations for each task.
- Relate tasks to business context and project objectives when possible.
- Encourage user feedback and collaboration during planning.
- Update the execution plan and documentation whenever there are changes in scope, requirements, or user preferences.

---

## Example Workflow

1. **User Prompt:** "Build a secure user registration API in Node.js"
2. **Agent Planning Mode:** Breaks down the solution into tasks (e.g., define data model, set up JWT authentication, implement input validation, document the API, write tests).
3. **Agent Presents Plan:** Details each task with approach, dependencies, expected outcome; requests user approval.
4. **User Approves:** User may approve, reject, or request changes to tasks.
5. **Agent Execution Mode:** Executes the approved tasks, documenting progress in the corresponding `tasks_[prompt-name].md` file in the memory bank.

---

## Summary

**With this rule active, the agent always operates transparently, collaboratively, and approval-driven, separating Planning from Execution. All solutions are documented and tasks are tracked, ensuring clarity, alignment, and full control for the user.**

---

**END OF FILE**

