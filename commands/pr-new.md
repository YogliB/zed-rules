# New PR Command

## Description

Create a pull request from the current Git branch using the GitHub CLI, following team conventions and ensuring commits comply with the Conventional Commit format.

## Trigger

User wants to create a pull request.

## Steps

1. **Environment Check**:
    - **CRITICAL**: Use **NON-SANDBOXED** terminal.
    - Request `network` permissions.
2. **Branch Check**: Ensure not on `main` or `master`. Alert if so.
3. **Handle Changes**:
    - If uncommitted changes exist, ask to stage/commit (Conventional Commit format) or continue.
    - **NEVER** commit/stage without explicit permission.
4. **Find Template**: Search `.github/`, `docs/`, or `.gitlab/` for `PULL_REQUEST_TEMPLATE.md`. Fail if missing.
5. **Determine Context**: Extract Jira ID, type, and description from branch/commits.
6. **Generate Content**:
    - Title: `CP-xxxxx: <conventional commit message>`
    - Body: Concise, bullet points, Jira link.
7. **Execute**: Run `gh pr create --web ...`
8. **Fallback**: If no template, use minimal bulleted body (Context, Changes, Jira link).

## Output Format

Terminal command execution and success message.

## Examples (Optional)

```bash
gh pr create \
  --title "CP-1234: feat(api) add auth" \
  --body-file .github/PULL_REQUEST_TEMPLATE.md \
  --web
```
