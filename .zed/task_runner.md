# Task Runner Guide

## Overview
This document provides guidelines for executing tasks defined in the `task_manager.json` file. The task runner helps ensure tasks are completed in the correct order and properly documented.

## Reading Tasks

Before executing tasks:

1. Load the `task_manager.json` file from the `.zed` directory
2. Check for available tasks that are marked as "pending"
3. Filter for tasks whose dependencies have been satisfied
4. Sort remaining tasks by priority ("high" → "medium" → "low")

## Task Execution Workflow

### 1. Select the Next Task

Choose the highest priority task with all dependencies satisfied. The task should be in "pending" status.

### 2. Update Task Status

Change the task status to "in_progress" in `task_manager.json` before beginning work.

### 3. Execute the Task

Follow these steps to execute a task:

- Review the task description, details, and test strategy
- If the task has subtasks:
  - Execute each subtask in the correct order (respecting dependencies)
  - Mark each subtask as "done" when completed
- Implement the task according to the details provided
- Document any deviations from the original plan
- Apply the test strategy to verify the task is complete

### 4. Document Results

For each completed task:

- Create a brief summary of implementation details
- Note any challenges encountered and solutions applied
- Document any configuration changes made
- Record performance metrics if applicable
- List any remaining issues or follow-up items

### 5. Update Task Status

When a task is complete:

- Update its status to "done" in `task_manager.json`
- Check if this completion unblocks any dependent tasks
- Update the CHANGELOG.md with a summary of the completed work

## Task Status Tracking

Task status follows this lifecycle:

- **pending**: Task is defined but not started
- **in_progress**: Task is currently being worked on
- **done**: Task is completed and verified
- **deferred**: Task is postponed for a future iteration

## Handling Dependencies

- Never start a task unless all its dependencies are marked as "done"
- If a dependency task is blocked, consider:
  - Breaking the dependency if it's not strictly necessary
  - Helping to complete the blocking task first
  - Requesting a reprioritization of tasks

## Progress Reporting

Maintain clear visibility on task progress:

- Update task status promptly in `task_manager.json`
- For long-running tasks, consider adding progress notes
- Document blockers or issues that prevent task completion
- Periodically review overall project progress

## Task Modification During Execution

If a task needs to be modified during execution:

1. Document the reason for the change
2. Update the task details in `task_manager.json`
3. If necessary, create new subtasks
4. Ensure dependencies remain valid
5. Update the test strategy if needed

## Best Practices

1. **Follow the dependency chain**: Always respect task dependencies
2. **Update status promptly**: Keep `task_manager.json` up to date
3. **Document thoroughly**: Record all significant implementation details
4. **Verify completion**: Always apply the test strategy
5. **Communicate blockers**: Report any issues that prevent task completion
6. **Respect priorities**: Focus on high-priority tasks first
7. **Close the loop**: Ensure all updates are reflected in documentation

## Upon Completion of All Tasks

When all tasks are complete:

1. Perform a final review of all deliverables
2. Update the project documentation to reflect all changes
3. Create a summary report of completed work and any outstanding items
4. Update the CHANGELOG.md with a comprehensive list of changes
5. Consider creating new tasks for future improvements