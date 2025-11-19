# Planning Rules Command

## Description

Defines the core rules and guidelines for creating valid, executable plans.

## Trigger

User asks about planning rules or during plan validation.

## Steps

1. **Core Requirements**: Plan must be fully executable with atomic, testable TODOs.
2. **Clarification**: Ensure ambiguity is <10% before planning and <5% before acting.
3. **Improvements**: Identify refactors, performance, or security wins before finalizing.
4. **Complexity Check**:
    - If TODOs > 30, Depth > 3, or High Risk > 5: **Split** into Masterplan + Sub-plans.
5. **Template Usage**: Read and enforce the standard planning template at `templates/plan.md`.
6. **Agent Rules**: 95% TODO coverage, consistent Markdown, no VCS steps in plan.

## Output Format

Text describing the rules or the Planning Template from `templates/plan.md`.

## Examples (Optional)

See `templates/plan.md` for the structure.
