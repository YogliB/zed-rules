# Before PR Command

**Purpose:**
Run this command before creating a pull request to ensure the current **feature branch** is clean and that **only the code changed in this branch** is validated and fixed.

---

### 🧩 Project Detection

The agent automatically detects the project type:

- **UI Projects** → `package.json`
- **Backend Python Projects** → `pyproject.toml`

---

### ⚙️ Commands

**UI Projects**

```bash
npm run verify
npm run test:ci:unit:coverage
```

**Backend Python Projects**

```bash
poetry run cybr pr
poetry run bandit
```

---

### 🧠 Agent Behavior Rules

- Run on **current feature branch**, not `main` or `master`.
- Stop on first failure.
- **Do not open a PR** — only validate and optionally auto-fix.
- **Scope all actions to changed files only.**

#### Determining Changed Files

The agent identifies changed files using:

```bash
git diff --name-only origin/main...HEAD
```

Only these files are linted, formatted, tested, or fixed.

#### Fixing and Staging

- Auto-fixes (e.g. Prettier, Black, isort) are **applied only to changed files**.
- After successful fixes, the agent **auto-stages them**:

  ```bash
  git add <changed-files>
  ```

- No unrelated files should be modified or committed.

#### Test & Coverage Scope

- Unit tests must pass for all test suites.
- Coverage thresholds apply **only to tests related to changed code**.
- Global coverage regressions trigger a **warning**, not a failure.

#### Handling Pre-existing Issues

- If lint or security tools detect unrelated issues:

  - **Log them**, do not fix.
  - Mark them as “legacy issues.”
  - Continue if changed files pass all checks.

---

### 🧾 Command Details

**UI Projects**

- `npm run verify`: ESLint, Prettier, Stylelint
- `npm run test:ci:unit:coverage`: Unit tests + coverage report

**Backend Python Projects**

- `poetry run cybr pr`: pre-commit checks (black, isort, pylint, etc.)
- `poetry run bandit`: security scanning

---

### ✅ Expected Results

**UI Projects**

- ESLint, Stylelint, Prettier pass for changed files
- Tests and coverage succeed
- Console clean of new warnings or errors

**Backend Python Projects**

- All pre-commit checks pass for changed files
- High code quality and consistent style
- No new vulnerabilities introduced
