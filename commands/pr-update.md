# Update PR Command

## Description

Update an existing pull request's title and description to reflect the current branch state, utilizing smart merging to preserve manual edits.

## Trigger

User wants to update an existing pull request.

## Steps

1. **Environment Check**:
    - **CRITICAL**: Use **NON-SANDBOXED** terminal.
    - Request `network` permissions.
2. **Branch Check**: Ensure not on `main` or `master`.
3. **Handle Changes**: Ask to stage/commit uncommitted changes.
4. **Validate**:
    - Prompt for PR number.
    - Verify PR exists and belongs to current branch (`gh pr view`).
5. **Find Template**: Locate `PULL_REQUEST_TEMPLATE.md`. Fail if missing.
6. **Smart Merge**:
    - Fetch existing body (`gh pr view ... --json body`).
    - Regenerate template sections with new context.
    - **Preserve** manual additions/non-template content.
7. **Execute**: Run `gh pr edit <number> ...`

## Output Format

Terminal command execution and success message.

## Examples (Optional)

```bash
gh pr edit 123 \
  --title "CP-1234: feat(api) updated auth" \
  --body "<merged-content>"
```
