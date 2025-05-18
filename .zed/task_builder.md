# Task Builder Guide

## Overview
This document provides guidelines for creating and managing tasks in the task management system. Tasks are stored in the `task_manager.json` file located in the `.zed` folder.

## Creating Tasks

### Task Structure
Each task in the `task_manager.json` file should have the following structure:

```json
{
  "id": 1,
  "title": "Task Title",
  "description": "Brief description of the task",
  "status": "pending",
  "dependencies": [2, 3],
  "priority": "high",
  "details": "Detailed implementation instructions...",
  "testStrategy": "How to verify the task is complete",
  "subtasks": []
}
```

### Task Fields

- **id**: Unique identifier for the task (numeric, can include decimal points for subtasks)
- **title**: Brief, descriptive title of the task
- **description**: Concise description of what the task involves
- **status**: Current state of the task (options: "pending", "in_progress", "done", "deferred")
- **dependencies**: IDs of tasks that must be completed before this task
- **priority**: Importance level of the task (options: "high", "medium", "low")
- **details**: In-depth implementation instructions
- **testStrategy**: Verification approach for determining task completion
- **subtasks**: List of smaller, more specific tasks that make up the main task

## Breaking Down Tasks

When a task is too complex, break it down into subtasks:

1. Create a main task with a unique ID (e.g., 5)
2. Add subtasks with decimal IDs (e.g., 5.1, 5.2, 5.3)
3. Define dependencies between subtasks to establish order

### Subtask Example

```json
{
  "id": 5,
  "title": "Implement Feature X",
  "description": "Develop feature X for the system",
  "status": "pending",
  "dependencies": [3, 4],
  "priority": "high",
  "details": "Implementation details for feature X",
  "testStrategy": "Test strategy for feature X",
  "subtasks": [
    {
      "id": 5.1,
      "title": "Design component A",
      "status": "pending",
      "dependencies": []
    },
    {
      "id": 5.2,
      "title": "Implement component A",
      "status": "pending",
      "dependencies": [5.1]
    },
    {
      "id": 5.3,
      "title": "Test component A",
      "status": "pending",
      "dependencies": [5.2]
    }
  ]
}
```

## Managing Dependencies

- Dependencies are represented by task IDs
- A task should not be started until all its dependencies are marked as "done"
- Dependencies can be visualized as: ✅ (completed) or ⏱️ (pending)
- Circular dependencies should be avoided

## Task Prioritization

Assign priorities to help determine the order of task execution:

- **high**: Critical tasks that block progress
- **medium**: Important tasks that should be done soon
- **low**: Tasks that can be deferred if necessary

## Adding New Tasks

To add a new task:

1. Determine the next available task ID
2. Fill in all required fields
3. Identify dependencies on existing tasks
4. Set appropriate priority
5. Add to the `tasks` array in `task_manager.json`

## Best Practices

1. **Be specific**: Tasks should be clear and unambiguous
2. **Set realistic dependencies**: Only add dependencies that are truly required
3. **Provide detailed instructions**: The "details" field should contain enough information for someone to implement the task
4. **Define verification methods**: Always include a test strategy
5. **Update status consistently**: Keep the status field updated as tasks progress
6. **Review periodically**: Regularly review tasks for relevancy and completeness
7. **Document changes**: Update the CHANGELOG.md when modifying tasks

## Task Validation

Periodically validate the task list for:
- Invalid dependencies
- Circular dependencies
- Missing required fields
- Inconsistent status updates