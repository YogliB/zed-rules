## Purpose

Convert the active conversation (tasks, findings, and conclusions) into a clear planning prompt for the agent — suitable for Plan Mode execution.

## Behavior

- Uses **entire current conversation history** as input.
- Produces **only** the planning prompt (no plan execution).
- Output should be **ready to paste** into Plan Mode.

## Output Requirements

- **Title** – concise summary of the conversation’s main goal or task.
- **Context** – distilled key details, findings, or decisions from the discussion.
- **Objective** – what the plan should achieve next.
- **Constraints** – any known limitations, assumptions, or rules.
- **Deliverables** – expected outputs or artifacts from the plan.

## Example Output

```
# Task

Investigate why API responses are missing `userRole` in production.

# Context

- Bug reproduced via `/users/me` endpoint.
- Local works, production fails.
- Logs show null value returned from DB query.
- Root cause suspected: missing join in ORM model.

# Objective

Plan the fix and validation steps to ensure `userRole` is always included.

# Constraints

- Avoid schema migrations.
- Use minimal ORM changes.

# Deliverables

- Implementation strategy.
- Verification steps.
- Risk assessment.
```
