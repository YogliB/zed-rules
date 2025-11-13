# Merge Conflict Resolution Command

## Purpose:

Ensure consistent, clean, and context-aware resolution of merge conflicts.

## Rules:

1. Analyze both sides of the conflict (`HEAD` vs. incoming changes) and the surrounding context.
2. Preserve **intent** over syntax — prioritize logic and clarity.
3. Keep **existing style and patterns** consistent with the file.
4. If uncertainty > **5%**, pause and ask **clarifying questions** before proceeding.
5. Never modify unrelated code or reformat entire files.
6. After resolving, run the appropriate **lint/test/format** commands to verify.
7. Summarize what was changed and why in a **short note** at the end.

## Command Example:

`/conflicts.md solve the merge conflicts in the current branch`
