# Create Tasks Advanced

## Description

Create comprehensive backlog tasks for a given request, filling all available fields including title, description, plan, acceptance criteria, priority, notes, assignee, and labels.

## Trigger

When the user requests to create tasks for a complex or high-priority request requiring full detail and metadata.

## Steps

1. Analyze the user's request to identify all relevant tasks needed to fulfill it, considering dependencies, risks, and scope.
2. For each identified task, determine:
    - Clear, concise title
    - Detailed description explaining purpose, context, and impact
    - Comprehensive implementation plan with specific, actionable steps
    - Thorough acceptance criteria for verification
    - Priority level (high, medium, low)
    - Implementation notes with additional context or considerations
    - Assignee if known
    - Relevant labels for categorization
3. Use the backlog task create command to create each task with the title.
4. Use backlog task edit to add all fields: description, plan, acceptance criteria, priority, notes, assignee, labels.
5. If dependencies exist between tasks, set them using --depends-on.
6. Confirm creation by listing the task IDs, titles, and all filled fields.
7. Do not start implementing the tasks until explicit approval from the user.

## Output Format

- Task [ID]: [Title] ([Priority])
    - Description: [Full description]
    - Plan: [Detailed steps]
    - Acceptance: [Criteria]
    - Notes: [Additional info]
    - Assignee: [Name]
    - Labels: [List]

## Examples

**Input:** Create advanced tasks for refactoring the authentication system.

**Output:**

- Task 100: Refactor Auth Module (High)
    - Description: Overhaul the authentication module for better security and maintainability.
    - Plan: 1. Audit current code, 2. Design new structure, 3. Implement changes, 4. Test thoroughly.
    - Acceptance: All tests pass, security audit clean, no breaking changes.
    - Notes: Coordinate with security team.
    - Assignee: security-lead
    - Labels: security, refactor
