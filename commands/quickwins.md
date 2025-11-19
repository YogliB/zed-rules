# Quick Wins Command

## Description

Suggest **up to 3 quick-win improvements** (≤1h each) across the **entire workspace** unless a scope is specified.

## Trigger

User asks for "quick wins" or improvements.

## Steps

1. **Identify Improvements**: Look for bugs, refactoring opportunities, performance issues, readability improvements, missing tests, or config tweaks.
2. **Present Options**: For each option, provide:
    - **Idea:** Short description.
    - **Snippet:** Minimal illustrative code or config (if relevant).
    - **Pros / Cons:** Brief, balanced (impact, risk).
3. **Recommend**: Provide **1 clear recommendation** optimized for impact vs. effort and low risk.
4. **Wait**: Stop after presenting and wait for user choice. Do not apply changes automatically.

## Output Format

Markdown list of options, followed by a recommendation.

## Examples (Optional)

**Option 1: Guard null inputs in parser (bug)**

- **Idea:** Add early-return for `null/undefined` payloads.
- **Snippet:**

```ts
export function parse(input?: string) {
	if (!input) return EMPTY_RESULT;
	// existing logic...
}
```
