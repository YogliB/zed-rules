# Plan from Conversation Command

## Description

Convert the active conversation (tasks, findings, and conclusions) into a clear planning prompt for the agent — suitable for Plan Mode execution.

## Trigger

User asks to create a plan based on the current discussion.

## Steps

1. **Analyze History**: Review the entire conversation for goals, tasks, findings, and decisions.
2. **Distill**: Extract key details and ignore irrelevant chatter.
3. **Format**: Create a structured prompt with:
    - **Title**: Concise summary.
    - **Context**: Key background details.
    - **Objective**: What to achieve.
    - **Constraints**: Limitations or rules.
    - **Deliverables**: Expected outputs.
4. **Output Only**: Do NOT execute the plan. Just provide the prompt.

## Output Format

Markdown block ready to be pasted into Plan Mode.

## Examples (Optional)

```markdown
# Task

Investigate why API responses are missing `userRole`.

# Context

- Bug reproduced in prod, works locally.
- Logs show null DB value.

# Objective

Plan fix and validation steps.

# Constraints

- Minimal ORM changes.

# Deliverables

- Fix implementation.
- Verification steps.
```
