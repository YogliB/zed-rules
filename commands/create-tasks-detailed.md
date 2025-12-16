# Create Tasks Detailed

## Description

Create detailed backlog tasks for a given request, filling fields like title, description, plan, and acceptance criteria.

## Trigger

When the user requests to create tasks for a request and specifies a detailed level of detail, or by default for standard requests.

## Steps

1. Analyze the user's request to identify all relevant tasks needed to fulfill it.
2. For each identified task, determine:
    - Clear, concise title
    - Detailed description explaining purpose and context
    - Implementation plan with specific steps
    - Acceptance criteria for verification
3. Use the backlog task create command to create each task with the title.
4. Use backlog task edit to add description, plan, and acceptance criteria.
5. If dependencies exist between tasks, set them using --depends-on.
6. Confirm creation by listing the task IDs, titles, and key details.

## Output Format

- Task [ID]: [Title]
    - Description: [Brief summary]
    - Plan: [Key steps]
    - Acceptance: [Criteria]

## Examples

**Input:** Create detailed tasks for moving atomic component dirs to src/components.

**Output:**

- Task 024: Move atoms directory
    - Description: Consolidate atoms under components folder
    - Plan: Use move_path tool
    - Acceptance: Directory moved successfully
- Task 025: Move molecules directory
    - Description: Consolidate molecules under components folder
    - Plan: Use move_path tool
    - Acceptance: Directory moved successfully
- Task 026: Move organisms directory
    - Description: Consolidate organisms under components folder
    - Plan: Use move_path tool
    - Acceptance: Directory moved successfully
