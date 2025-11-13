## Purpose

Update **all status references** for a given PR in a masterplan markdown file, ensuring consistency across the entire document.
If a new status is **not provided**, infer it automatically from the GitHub PR state using the **GitHub CLI**.

## Behavior

- Ask clarifying questions **only if uncertainty >10%**.
- If a new status **is not given**, check the PR using the GitHub CLI (`gh pr view`).
- Map PR states (`OPEN`, `MERGED`, `CLOSED`, `DRAFT`, `READY_FOR_REVIEW`) to the closest plan status.
- Update **ALL** locations where the PR status appears (see "What Gets Updated" below).
- Include or update the PR link if missing.
- Save with consistent markdown formatting.

## What Gets Updated

When updating a PR status, search and update these locations:

1. **Implementation Status Table** (Section 2)

   - Update the status column for the PR row
   - Format: `| PR1 | repo-name | 🟠 Pending Review | [PR#N](url) | notes |`

2. **PR Section Header** (Section 3)

   - Update the status emoji in the PR section title
   - Format: `## PR1: [Title] — 🟠 Pending Review`

3. **PR Section Status Field** (Section 3)

   - Update the status description in the PR details
   - Format: `**Status:** Open and awaiting review (REVIEW_REQUIRED)`

4. **Deployment Strategy Stage Headers** (Section 5)

   - Update stage headers that reference this PR
   - Format: `### Stage 1: SDK Deployment (PR1 - repo) — 🟠 Pending Review`

5. **Cross-Repository Version Alignment Table** (Section 5)

   - Update any status indicators in the notes column
   - Format: Notes column may contain status emoji or status text

6. **Other References**
   - Search for other mentions of the PR throughout the document
   - Update any status-related text to maintain consistency

## PR → Status Mapping

| PR State          | Plan Status    | Emoji | Notes                |
| ----------------- | -------------- | ----- | -------------------- |
| OPEN (draft)      | Planned        | 🟣    | Draft PR created     |
| OPEN (in review)  | Pending Review | 🟠    | Awaiting review      |
| OPEN (active)     | In Progress    | 🟡    | Work ongoing         |
| MERGED            | Completed      | 🟢    | Fully merged         |
| CLOSED (unmerged) | Cancelled      | ⚫    | Closed without merge |
| READY_FOR_REVIEW  | Ready          | 🔵    | PR ready for review  |

## Steps

1. **Identify the target plan file and PR number**
2. **Locate the PR link** (or prompt for it if missing)
3. **Determine the new status:**

   - If manual status provided → use it
   - Otherwise: Run `gh pr view <PR_URL> --json state,isDraft,mergedAt,reviewDecision`
   - Map PR state to plan status using the table below

4. **Update ALL status references:**

   - Main Implementation Status Table (row for this PR)
   - PR section header (`## PR[N]: [Title] — [Status]`)
   - PR section status field (`**Status:** [description]`)
   - Deployment Strategy stage headers (if applicable)
   - Cross-Repository Version Alignment Table (if applicable)
   - Any other status mentions found via search

5. **Update PR link if missing**

6. **Save with consistent formatting**

## Search Strategy

To find all status references for a PR:

1. Search for `PR[N]` (e.g., `PR1`) to find all mentions
2. Check each match to see if it contains status information
3. Update status where found, maintaining the existing format
4. Use context-aware updates:
   - Table rows: Update status column only
   - Headers: Update emoji/text after `—`
   - Status fields: Update entire description
   - Notes: Update embedded status text/emoji

## Example

```bash
# Check PR status from GitHub and update all references
update-masterplan-status @ai-agent-trends-implementation.md PR1

# Manually set status
update-masterplan-status @ai-agent-trends-implementation.md PR1 completed

# Update with PR link provided
update-masterplan-status @ai-agent-trends-implementation.md PR1 https://github.com/org/repo/pull/123
```

## Example Updates

Given PR1 status change from "Ready for Merge" to "Pending Review":

### Before:

```markdown
| PR1 | repo-name | ✅ Ready for Merge | [PR#128](url) | SDK changes |

## PR1: SDK Changes — ✅ Ready for Merge

**Status:** PR created and ready for review

### Stage 1: SDK Deployment (PR1) — ✅ Ready for Merge

| 1 | PR1 | SDK v2.1 | ✅ Ready for merge |
```

### After:

```markdown
| PR1 | repo-name | 🟠 Pending Review | [PR#128](url) | SDK changes |

## PR1: SDK Changes — 🟠 Pending Review

**Status:** Open and awaiting review (REVIEW_REQUIRED)

### Stage 1: SDK Deployment (PR1) — 🟠 Pending Review

| 1 | PR1 | SDK v2.1 | 🟠 Pending review (41 tests passing) |
```

## Handling Legacy Masterplans

Some masterplans may have been created before the standardized template existed. These may have:

- Different section structures
- Additional status tables not in the standard template
- Non-standard header formats
- Custom status indicators

**Approach for legacy plans:**

1. **Identify the plan structure** - Read through to understand its organization
2. **Search comprehensively** - Use grep/search to find ALL mentions of the PR
3. **Update what's found** - Adapt to the existing format rather than forcing standard format
4. **Maintain consistency** - Keep the same style/format used in that specific plan
5. **Document variations** - Note any non-standard patterns found

**Common legacy patterns:**

- Multiple status tables (e.g., one for implementation, one for deployment coordination)
- Stage-specific status tracking in deployment sections
- Status in multiple formats (emoji + text, text only, etc.)
- Custom status categories beyond the standard set

**Example legacy patterns found in AI Agent Trends plan:**

- Cross-Repository Version Alignment table with status in notes column
- Deployment Strategy stages with status in section headers
- Stage-level checklists with completion status (✅/⏸️)

When updating legacy plans, search for the PR identifier (e.g., "PR1") and carefully update each occurrence based on context.

### Status Color Map

| Status            | Emoji       | Meaning               |
| ----------------- | ----------- | --------------------- |
| 🟢 Completed      | Green       | Work done             |
| 🟡 In Progress    | Yellow      | Active work           |
| 🟠 Pending Review | Orange      | Awaiting feedback     |
| 🔵 Ready          | Blue        | Ready for next step   |
| ⏸️ Not Started    | Grey        | Not yet started       |
| 🔴 Blocked        | Red         | Waiting on dependency |
| ⚪ On Hold        | White       | Paused temporarily    |
| 🟣 Planned        | Purple      | Scheduled work        |
| ⚫ Cancelled      | Black       | Dropped task          |
| 🧪 Testing        | Teal        | In QA phase           |
| 🧩 Partial        | Light Green | Partially done        |
| 🌀 Refactoring    | Indigo      | Under improvement     |
