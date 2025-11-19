# Commit Command

## Description

Create a commit that fully complies with Conventional Commit Guidelines, using auto-generated titles based on branch name and file changes.

## Trigger

User wants to commit changes.

## Steps

1. **Check Staged Files**:
    - If none, ask: _"No files staged. Stage all modified files?"_
    - If yes → `git add -A`
    - If no → abort.
2. **Extract Context**:
    - Get branch name (`git rev-parse --abbrev-ref HEAD`).
    - Extract JIRA ID (pattern: `[A-Z]+-\d+`).
    - Infer type/scope (`src/api` -> `feat(api)`, `tests/` -> `test`, etc.).
    - Generate description from changed files.
3. **Build Title**: Format as `JIRA_ID: type(scope) description`.
4. **Validate**: Ensure ≤ 72 characters, no body/footer. Show preview if elements are missing.
5. **Commit**: Run `git commit -m "<generated_title>"`.
6. **Output**: Print success message.

## Output Format

`✅ Committed: <generated_title>`

## Examples (Optional)

```
✅ Committed: CP-2345: fix(api) handle null values in response
```
