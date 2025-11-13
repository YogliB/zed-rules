# Planning Command

## Core Principle

Plans must be **fully executable** with a **complete TODO list** (atomic, testable steps). Missing TODO = invalid.

---

## Clarifications

- Pre-plan: reduce ambiguity **<10%** via grouped questions (scope, risk, deps).
- Post-approach: clarify technical details until **<5%** ambiguity.

---

## Improvement Detection

Before finalizing, list **Improvement Opportunities**:

- Refactor, architecture, quality, performance, security.
- Include scope + rationale; ask: **Apply? (Y/N)**.

---

## Plan Template

1.  **ID / Version**
2.  **Goal**
3.  **Scope**
4.  **Risks**
5.  **Dependencies / Constraints**
6.  **Priority / Ordering**
7.  **Logging / Observability**
8.  **✅ TODO List** (mandatory, full breakdown, nested checkboxes)
9.  **Testing / Docs / Acceptance**
10. **Fallback**
11. **References**

---

## Agent Rules

- TODO coverage ≥95%.
- Enforce clarifying thresholds.
- Prefer authoritative sources.
- Detect/report improvements pre-final.
- Keep sections coherent, Markdown consistent.
- No VCS steps.
- Optimize for traceability & autonomy.
