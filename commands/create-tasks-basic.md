# Create Tasks Basic

## Description

Create basic backlog tasks for a given request, filling only essential fields like title and description.

## Trigger

When the user requests to create tasks for a request and specifies a basic level of detail.

## Steps

1. Analyze the user's request to identify all relevant tasks needed to fulfill it.
2. For each identified task, determine a clear, concise title and brief description.
3. Use the backlog task create command to create each task with the title.
4. Use backlog task edit to add the description.
5. If dependencies exist between tasks, set them using --depends-on.
6. Confirm creation by listing the task IDs and titles.

## Output Format

- Task [ID]: [Title] - [Brief status]

## Examples

**Input:** Create basic tasks for moving atomic component dirs to src/components.

**Output:**

- Task 024: Move atoms directory - Created
- Task 025: Move molecules directory - Created
- Task 026: Move organisms directory - Created
