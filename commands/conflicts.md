# Conflicts Command

## Description

Ensure consistent, clean, and context-aware resolution of merge conflicts.

## Trigger

User asks to resolve merge conflicts in the current branch.

## Steps

1. **Analyze**: Examine both sides (`HEAD` vs. incoming) and the surrounding context.
2. **Resolve**:
    - Prioritize **intent** over syntax.
    - Keep **existing style and patterns** consistent.
    - **Pause** if uncertainty > 5% and ask clarifying questions.
3. **Verify**: Run appropriate lint, test, or format commands to check validity.
4. **Summarize**: Provide a short note explaining what was changed and why.

## Output Format

Resolved files + a summary note.

## Examples (Optional)

`/conflicts.md solve the merge conflicts in the current branch`
