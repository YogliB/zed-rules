# Alternatives Command

## Description

Suggest **up to 3 viable alternatives** for code or design decisions before committing to an implementation.

## Trigger

User asks for alternatives, options, or "better ways" to solve a problem.

## Steps

1. **Identify Options**: brainstorm distinct approaches (e.g., different patterns, libraries, or architectural choices).
2. **Present**: For each option, provide:
    - **Idea**: Short description.
    - **Snippet**: Minimal code example (if relevant).
    - **Pros / Cons**: Brief, balanced assessment.
3. **Recommend**: Provide **1 clear recommendation** based on clarity and maintainability.
4. **Wait**: Stop after presenting and wait for the user's choice. **Do not edit files.**

## Output Format

Markdown list of options followed by a recommendation.

## Examples (Optional)

**Option 1: Shared helper function**

- **Idea:** Extract common logic
- **Snippet:**

```ts
function processData(d: Data[]) {
	return d.filter(validate).map(transform);
}
```

- **Pros:** DRY, consistent
- **Cons:** Adds indirection

**Recommendation:** Option 1 — best balance.
