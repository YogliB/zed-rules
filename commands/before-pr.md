# Before PR Command

## Description

Run validation checks (linting, testing, security) on the current feature branch to ensure it is clean before creating a pull request. Scopes checks to changed files only.

## Trigger

User runs "before pr" or wants to validate the branch before creating a PR.

## Steps

1. **Detect Project Type**:
    - **UI Projects**: Look for `package.json`.
    - **Backend Python Projects**: Look for `pyproject.toml`.
2. **Identify Scope**:
    - Find changed files using `git diff --name-only origin/main...HEAD`.
    - Apply actions **only** to these files.
3. **Execute Commands**:
    - **UI**: Run `npm run verify` (ESLint, Prettier) and `npm run test:ci:unit:coverage`.
    - **Backend**: Run `poetry run cybr pr` (Black, Isort, Pylint) and `poetry run bandit`.
4. **Handle Auto-Fixes**:
    - Apply fixes (Prettier/Black) **only** to changed files.
    - Auto-stage successful fixes: `git add <changed-files>`.
    - **Do not** modify unrelated files.
5. **Result Handling**:
    - **Success**: All checks pass for changed files.
    - **Failure**: Stop on first error.
    - **Legacy Issues**: Log unrelated issues but do not block if changed files are clean.

## Output Format

Terminal output of the executed commands and a final success/failure status.

## Examples (Optional)

None provided.
