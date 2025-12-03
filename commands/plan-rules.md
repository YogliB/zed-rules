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
    - If TODOs > 30, Depth > 3, High Risk > 5, **or scope is too large for a single pull request**: **Alert** that this should be a masterplan.
5. **Template Usage**: Read and enforce the standard planning template at `templates/plan.md`.
6. **Agent Rules**: 95% TODO coverage, consistent Markdown, no VCS steps in plan.
7. **Storage Instruction**: All finalized plans must be written to `docs/plans/`.
8. **Completion Action**: Suggest deleting the plan after successful execution.

## Output Format

Text describing the rules or the Planning Template from `templates/plan.md`.

## Examples

See `templates/plan.md` for the structure.
