# Investigate Command

## Description

Diagnose issues and errors systematically **without writing code** or modifying the system state.

## Trigger

User asks to investigate a bug, error, or issue.

## Steps

1. **Assess**: Understand the issue, context, and symptoms.
2. **Reproduce**: Attempt to replicate the issue to isolate its scope.
3. **Analyze**:
    - Use **Read-only** tools: `cat`, `ls`, `grep`, `find`, logs.
    - Check code, configs, environment variables, and dependencies.
    - **Prohibited**: Write/modify files, destructive commands, installs.
4. **Verify**: Confirm the root cause and rule out alternatives.
5. **Report**: Document findings and suggestions.

## Output Format

- **Summary**: Problem, symptoms, impact.
- **Steps**: What was checked and what was found.
- **Root Cause**: Evidence and contributing factors.
- **Related Areas**: Additional checks performed.
- **Fix Suggestions**: Proposed code changes and risks.
- **Recommendations**: Immediate and preventive actions.
- **Confidence**: High/Medium/Low.

## Examples (Optional)

None provided.
