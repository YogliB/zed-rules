# New Masterplan Command

## Description

Create a comprehensive Masterplan for multi-repo work, sequential PRs, phased rollouts, high-risk changes, or major architecture.

## Trigger

User starts a complex feature, multi-repo task, or high-risk change.

## Steps

1. **Ask First**: Reduce ambiguity < 5% (Scope, Dependencies, Rollout, Risk).
2. **Detect Improvements**: Look for cross-repo refactors or quality wins. Prompt to include them.
3. **Draft Plan**: Read the template at `templates/masterplan.md` and use it as the base.
    - Fill in all sections: Overview, Implementation Status, Detailed PRs, Deployment Strategy, Success Criteria.
4. **Testing Policy**: Ensure tests are integrated with related changes (no standalone test PRs).
5. **Review**: Validate precise paths, snippets, and explicit dependencies.
6. **Save**: Write to `docs/plans/in-progress/[feature-name].md`.

## Output Format

A new Markdown file containing the Masterplan based on `templates/masterplan.md`.

## Examples (Optional)

See `templates/masterplan.md` for the full template structure.
