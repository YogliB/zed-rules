# Coding Rules

## Principle

Code must **explain itself** — no comments.

## Guidelines

- Use **clear, intention-revealing names**.
- Keep functions **small, focused, testable**.
- Prefer **simple control flow** (early returns).
- Express intent via **types & tests**.
- Document design in **Markdown**, not code.
- Follow **Clean Code**: clarity > cleverness.
- Don't over-engineer; YAGNI.

### Checklist

- **SRP**: one purpose per unit.
- **DRY**: no duplication.
- **KISS**: simple > complex.
- **Pure**: avoid side effects.
- **Readable > Optimal**.
- **Consistent style**.

## Naming

- Functions = verbs (`fetchUserProfile`)
- Types = nouns (`RetryPolicy`)
- Clarity > brevity (`timeoutMs` not `t`)
- Include units/context (`fileSizeBytes`)

## Comments

- Allowed: auto-generated headers/licenses.
- Forbidden: inline comments, docstrings, TODO/FIXME.
