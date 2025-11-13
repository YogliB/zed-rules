## Purpose

Create a commit that fully complies with Conventional Commit Guidelines, using auto-generated titles based on branch name and file changes.

## Behavior

1. **Check staged files**

   - If none exist, ask:
     _"No files staged. Stage all modified files?"_

     - If yes → `git add -A`
     - If no → abort with message `"Aborted: No files staged."`

2. **Extract commit context**

   - Get current branch name via `git rev-parse --abbrev-ref HEAD`
   - Extract JIRA ID (pattern: `[A-Z]+-\d+`)
   - Infer type and optional scope:

     - `src/api` → `feat(api)`
     - `src/ui` or `components` → `feat(ui)`
     - `tests/` → `test`
     - `docs/` → `docs`
     - `scripts/`, `build/`, or `config/` → `chore`
     - Otherwise fallback to `refactor`

   - Generate description heuristically:

     - Use key nouns/verbs from changed filenames or directories (`user model`, `login flow`, `readme`, etc.)
     - If unclear, fallback to `"update files"`

3. **Build commit title**

   - Format:
     `JIRA_ID: type(scope) description`
   - Example:
     `CP-1234: feat(api) add JWT authentication`

4. **Validate**

   - Ensure ≤ 72 characters
   - Ensure no body or footer
   - If missing required elements, show preview and ask for confirmation before proceeding.

5. **Commit**

   - Run:
     `git commit -m "<generated_title>"`

6. **Output**

   - Print:
     `"✅ Committed: <generated_title>"`

---

### Example Output

```
✅ Committed: CP-2345: fix(api) handle null values in response
```
