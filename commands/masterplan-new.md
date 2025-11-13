## Purpose

Create a **comprehensive masterplan** for complex, multi-stage, or cross-repository initiatives that require detailed coordination, phased deployment, and thorough risk management.

Masterplans are more extensive than regular plans and are designed for:

- Multi-repository features
- Features requiring multiple sequential PRs
- Complex features with significant risk or coordination needs
- Features requiring phased rollouts with feature flags
- Major architectural changes

## Clarifying Questions

Ask clarifying questions until **ambiguity is under 5%**, focusing on:

### Scope & Requirements

- What is the primary goal and expected outcome?
- Which repositories are involved?
- What existing patterns should be followed?
- What are the acceptance criteria?
- Are there any constraints (performance, backward compatibility, etc.)?

### Dependencies & Integration

- What external systems or services are involved?
- What SDK or library versions are required?
- Are there database schema changes needed?
- What API contracts need to be maintained?

### Deployment & Rollout

- Is a phased rollout required?
- Should a feature flag be used?
- What is the deployment order across repositories?
- What environments need to be tested (DEV, STAGING, PROD)?

### Risk & Recovery

- What are the high-risk areas?
- What is the rollback strategy?
- What monitoring is needed?
- What are the potential breaking changes?

## Improvement Detection

During masterplan creation, as implementation details and architecture are explored, the agent should actively identify **improvement opportunities in the codebase, architecture, or implementation approach**.

### Types of Improvements to Detect

- **Cross-repository refactoring opportunities** – Duplicated logic across services, inconsistent patterns, shared code that should be extracted
- **Architectural patterns across multiple services** – Better service boundaries, improved API design, enhanced data flow patterns
- **Performance optimizations affecting multiple components** – Inefficient cross-service communication, unnecessary database queries, caching opportunities
- **Security or reliability improvements in deployment strategy** – Enhanced rollback mechanisms, better monitoring coverage, improved error handling across services
- **Code quality improvements spanning multiple PRs** – DRY violations across repositories, naming inconsistencies, unclear service contracts

### When to Alert

Alert the user **during masterplan creation**, after the initial draft is complete but before final presentation.

### How to Present Improvements

Include a dedicated **"Improvement Opportunities"** section in the masterplan with:

- Clear description of each improvement
- Scope affected (repositories, PRs, components, services)
- Rationale for why it improves the implementation
- Estimated impact (minor/moderate/significant)
- Which PR(s) the improvement would affect

Then prompt: **"Apply these improvements to the masterplan? (Y/N)"**

### User Decision

- Improvements become part of the masterplan **only if the user agrees** (responds Y/Yes)
- If user declines, proceed with the original masterplan
- If user partially agrees, clarify which improvements to include and adjust affected PRs accordingly

## Masterplan Template

Use this comprehensive structure for all masterplans:

### 1. Header & Metadata

```markdown
---
alwaysApply: false
---

# [Feature Name] Masterplan

## Overview

[2-3 paragraph summary of the feature, approach, and why this matters]

**Approach:** [Brief description of chosen approach]

**Total Estimated Time:** [X-Y hours]
**Number of PRs:** [N] PRs (across [M] repositories)
**Risk Level:** [Low/Medium/High] ([brief risk explanation])
**Repositories Involved:**

- [repo-1] (PR X, Y, Z)
- [repo-2] (PR N)
```

### 2. Implementation Status

**PR Numbering Rules:**

- PR numbers MUST be whole numbers (1, 2, 3, ...)
- PR numbers MUST always start with 1
- PR numbers MUST be sequential based on dependency order

```markdown
## Implementation Status

| PR  | Repository  | Status         | PR Link     | Notes                          |
| --- | ----------- | -------------- | ----------- | ------------------------------ |
| PR1 | [repo-name] | ⏸️ Not Started | -           | [description] - blocked by [X] |
| PR2 | [repo-name] | 🟡 In Progress | [PR#N](url) | [description]                  |
| PR3 | [repo-name] | 🟢 Completed   | [PR#N](url) | [description]                  |
```

**Status Icons:**

- 🟢 Completed
- 🟡 In Progress
- 🟠 Pending Review
- ⏸️ Not Started
- 🔴 Blocked
- ⚫ Cancelled

### 3. PR Details (One Section Per PR)

For each PR, include:

```markdown
## PR[N]: [PR Title] — [Status Icon]

**Repository:** [repo-name]

**PR Link:** [URL or "-"]

**Status:** [Current status]

**Estimated Time:** [X-Y hours] dev + [X-Y min] review

**Files to Modify/Create:**

- `path/to/file1.ext`
- `path/to/file2.ext`

**Changes:**

### 1. [Change description with code context]

File: `path/to/file.ext`

[Detailed explanation of what needs to change, including:]

- Line numbers or context (e.g., "Add after line 42")
- Code snippets showing before/after (use code blocks)
- Explanation of why this change is needed
- Any imports or dependencies to add

### 2. [Next change...]

**Acceptance Criteria:**

- [ ] Criterion 1
- [ ] Criterion 2
- [ ] Tests pass
- [ ] No breaking changes
- [ ] [etc.]

**Dependencies:**

- Blocked by: [PR numbers or "None"]
- Blocks: [PR numbers or "None"]
```

### 4. Risk Mitigation

```markdown
## Risk Mitigation

### [Risk Category 1]

**Concern:** [What could go wrong?]

**Analysis:**

- [Detailed analysis of the risk]
- [Metrics, numbers, or data supporting the analysis]

**Mitigation:**

- [Specific steps to mitigate]
- [Monitoring or alerting to add]
- [Fallback strategies]

**Recovery:**

- [How to recover if this risk materializes]

### [Risk Category 2]

...
```

### 5. Deployment Strategy

```markdown
## Deployment Strategy

**CRITICAL:** [Any critical deployment ordering or coordination notes]

### Stage 1: [First deployment stage]

**Repository:** [repo-name]
**PRs:** PR1

1. Deployment steps
2. Verification
3. Rollback criteria

### Stage 2: [Next deployment stage]

**Repository:** [repo-name]
**PRs:** PR2

1. Deployment steps
2. Verification
3. Rollback criteria

### Stage 3: [Continue for all stages...]

[Continue for all stages...]

### Cross-Repository Version Alignment

| Stage | PR  | [Repo 1] | [Repo 2] | [Repo 3] | Notes   |
| ----- | --- | -------- | -------- | -------- | ------- |
| 1     | PR1 | v1.0     | -        | -        | [notes] |
| 2     | PR2 | v1.1     | -        | -        | [notes] |
| 3     | PR3 | v1.1     | v2.0     | -        | [notes] |
```

### 6. Monitoring & Observability

```markdown
## Monitoring & Observability

### CloudWatch Metrics (or equivalent)

- [Metric 1 - what to monitor]
- [Metric 2 - expected values]

### CloudWatch Logs (or equivalent)

Monitor for:

**Success messages:**

- "[log message 1]" ([meaning])
- "[log message 2]" ([meaning])

**Error messages:**

- "[error pattern 1]" ([meaning])
- "[error pattern 2]" ([meaning])

### Alarms

- [Alarm 1 - condition and threshold]
- [Alarm 2 - condition and threshold]
```

### 7. Rollback Plan

```markdown
## Rollback Plan

### Quick Rollback (if applicable)

**If feature flag exists:**

1. Disable feature flag
2. Verify logs
3. Fix issues
4. Re-enable when ready

**Advantages:**

- Instant rollback
- Zero downtime
- Can be toggled per environment

### Full Rollback Strategy

**If [PR/Stage N] causes issues:**

1. [Specific rollback steps]
2. [Verification]
3. [What continues working]
4. [What stops working]

### Cross-Repository Rollback Order

If full rollback needed:

1. **First:** [Last deployed component - highest risk]
2. **Second:** [Next component]
3. **Last:** [First deployed component - lowest risk]

### Rollback Artifacts (Safe to Leave)

[List any artifacts that remain after rollback and why they're safe]
```

### 8. Success Criteria

```markdown
## Success Criteria

- [ ] All [N] PRs merged and deployed to production
- [ ] [Feature-specific success criterion 1]
- [ ] [Feature-specific success criterion 2]
- [ ] No performance regression ([metric] < [threshold])
- [ ] All tests passing with >= [X]% coverage
- [ ] Zero production incidents related to this feature
- [ ] [Monitoring criteria]
- [ ] [User-facing criteria]
```

### 9. Reference Implementation Examples

```markdown
## Reference Implementation Examples

### [Existing Pattern to Follow 1]

File: `path/to/reference/file.ext`
Lines: [X-Y] ([description])

### [Existing Pattern to Follow 2]

File: `path/to/reference/file.ext`
Lines: [X-Y] ([description])
```

### 10. Notes & Assumptions

```markdown
## Notes

### Implementation Approach

- [Key implementation decision 1]
- [Key implementation decision 2]

### Cross-Repository Coordination

- [Coordination note 1]
- [Coordination note 2]

### Data Model Details

- [Data model decision 1]
- [Data model decision 2]

### Risk Considerations

- [Risk consideration 1]
- [Risk consideration 2]

### Testing Strategy

- [Testing approach 1]
- [Testing approach 2]

### Assumptions Verified

- ✅ [Assumption 1]
- ✅ [Assumption 2]
- ❌ [Assumption 3 - needs verification]
```

## Execution Guidelines

### Before Creating the Plan

1. **Research existing patterns** - Search the codebase for similar implementations
2. **Verify assumptions** - Check that dependencies, enums, and helpers exist
3. **Identify all affected repositories** - Don't miss cross-repo dependencies
4. **Estimate realistically** - Include review time, not just dev time

### While Creating the Plan

1. **Be specific with file paths and line numbers** when possible
2. **Include code snippets** for complex changes (using proper code blocks)
3. **Show before/after context** for modifications
4. **Explain WHY** each change is needed, not just WHAT
5. **Link PRs in sequence** - show clear dependency chains
6. **Think about edge cases** - NULL values, empty results, tenant isolation
7. **Consider backward compatibility** - what breaks if this fails?
8. **Plan monitoring BEFORE deployment** - don't wait for issues

### PR Sequencing Rules

1. **Dependencies first** - SDK changes before implementation
2. **Backend before frontend** - API before UI
3. **Schema migrations early** - before code that uses new schema
4. **Tests alongside implementation** - or immediately after
5. **Feature flags before risky code** - enable safe rollouts
6. **GraphQL schema LAST** - after backend is fully ready

### Quality Checklist

Before finalizing the masterplan, verify:

- [ ] Improvement opportunities have been identified and presented to user
- [ ] All PRs have clear acceptance criteria
- [ ] Dependencies between PRs are explicit
- [ ] Risk mitigation covers all high-risk areas
- [ ] Rollback plan is specific and actionable
- [ ] Deployment order prevents breaking changes
- [ ] Monitoring covers success and failure cases
- [ ] Success criteria are measurable
- [ ] Time estimates include review time
- [ ] Code snippets are accurate and complete
- [ ] File paths and line numbers are precise (where known)

## Output Format

1. **Save the masterplan** to `.cursor/plans/[username]/[feature-name].md`
2. **Use consistent Markdown formatting**:
   - Headers: `##`, `###`, `####` for hierarchy
   - Code blocks: Use language tags (`python, `graphql, etc.)
   - Tables: Aligned and readable
   - Lists: Consistent bullet/numbering style
   - Checkboxes: `- [ ]` for incomplete, `- [x]` for complete
3. **Include the frontmatter**:
   ```markdown
   ---
   alwaysApply: false
   ---
   ```

## Plan Maintenance

After creating the masterplan:

1. **Update PR links** as PRs are created
2. **Update status icons** as work progresses (use `update-masterplan-status`)
3. **Document deviations** if implementation diverges from plan
4. **Add learnings** to Notes section as discovered
5. **Keep it current** - a stale plan is worse than no plan

## Example Usage

```
Create a masterplan for implementing real-time notifications across the platform,
involving changes to 3 repositories, requiring a new EventBridge rule,
Lambda functions, WebSocket connections, and GraphQL subscriptions.
```

The agent should:

1. Ask clarifying questions about scope, scale, dependencies
2. Research existing notification patterns in the codebase
3. Identify all affected repositories
4. Create a phased PR sequence with clear dependencies
5. Plan feature flag strategy for safe rollout
6. Define monitoring and alerting requirements
7. Document rollback procedures
8. Create the comprehensive masterplan document

## Anti-Patterns to Avoid

❌ **Don't:**

- Create masterplans for simple, single-PR features
- Skip risk analysis for "obvious" implementations
- Assume dependencies exist without verification
- Leave PR dependencies implicit
- Deploy schema changes before backend is ready
- Forget about monitoring until after deployment
- Use vague acceptance criteria ("works correctly")
- Skip rollback planning for "low risk" changes

✅ **Do:**

- Reserve masterplans for complex, multi-stage work
- Analyze risks even for familiar patterns
- Verify all assumptions before planning
- Make PR dependencies explicit with blockers
- Deploy backend fully before exposing APIs
- Plan monitoring during design phase
- Use measurable, testable acceptance criteria
- Always have a rollback plan, even for low-risk changes

---

**Remember:** A masterplan is a **living document**. Update it as the implementation progresses, discoveries are made, and learnings emerge. The goal is to make execution predictable, safe, and reversible.
