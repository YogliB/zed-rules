# Alternatives Command

### Purpose

Suggest **up to 3 viable alternatives** for code/design before committing.

### Behavior

1.  For each option:
    *   **Idea:** short description
    *   **Snippet:** minimal example (if relevant)
    *   **Pros / Cons:** brief, balanced
2.  Give **1 clear recommendation** based on clarity & maintainability.
3.  **Stop after presenting**; wait for user choice.
4.  **No diffs or file edits.**
5.  Ask clarifying questions only if uncertainty >10%.

### Output Example

**Option 1: Shared helper function**

*   **Idea:** Extract common logic
*   **Snippet:**

```ts
function processData(d: Data[]) {
  return d.filter(validate).map(transform);
}
```

*   **Pros:** DRY, consistent
*   **Cons:** Adds indirection

**Recommendation:** Option 1 — best balance.
