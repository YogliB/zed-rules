# [Feature] Masterplan

**Overview:** [2–3 short sentences]
**Approach:** [brief]
**Est. Time:** [X–Yh incl. review]
**PRs:** [N] across [M] repos
**Risk:** [Low/Med/High – why]
**Repos:** [repo-1], [repo-2], ...

## Implementation Status

> PRs: whole numbers, start at 1, sequential by dependencies.

| PR  | Repo   | Status | Link | Notes |
| --- | ------ | ------ | ---- | ----- |
| 1   | repo-a | ⏸️     | -    | ...   |
| 2   | repo-b | 🟡     | ...  | ...   |
| 3   | repo-a | 🟢     | ...  | ...   |

Status: 🟢 done · 🟡 in‑progress · 🟠 review · ⏸️ not‑started · 🔴 blocked · ⚫ canceled

## PR[N]: [Title] — [Status Icon]

**Repo:** [name] · **Link:** [-/URL] · **ETA:** [X–Yh dev + X–Ym review]
**Files:** `path/one`, `path/two`

**Changes:**

1. [what/why] — File: `path.ext`
    - [line/context], before→after code
    - deps/imports

**Acceptance:**

- [ ] Criteria 1
- [ ] Criteria 2
- [ ] Tests updated/added (integrated)
- [ ] No breaking changes
- [ ] All checks pass

**Dependencies:** Blocked by [PRs]/None · Blocks [PRs]/None

## Risk Mitigation

**[Risk Category]:** concern → analysis → mitigation → recovery.

## Deployment Strategy

**CRITICAL:** [ordering/coordination]

**Stage 1:** Repo [ ] · PRs: [ ]

1. deploy 2) verify 3) rollback

**Stage 2:** ...

**Cross‑Repo Version Map**
| Stage | PR | repo‑1 | repo‑2 | repo‑3 | Notes |
| ----: | -- | ------ | ------ | ------ | ----- |
| 1 | 1 | v1.0 | - | - | ... |

## Monitoring & Observability

**Metrics:** [name → expected]
**Logs:** success: ["..."], errors: ["..."]
**Alarms:** [condition → threshold]

## Rollback

**Quick (flag):** disable → verify → fix → re‑enable.
**Full:** if [PR/Stage N] fails → steps, verify, what works/stops.
**Order:** first: last‑deployed/highest‑risk → ... → last: lowest‑risk.
**Artifacts safe to keep:** [list]

## Success Criteria

- [ ] All [N] PRs merged+prod
- [ ] Feature criteria 1/2
- [ ] No perf regression ([metric] < [thr])
- [ ] Tests ≥ [X]% & green
- [ ] 0 prod incidents
- [ ] Monitoring meets SLOs
- [ ] User‑facing criteria met

## References

- [Pattern 1] `path/file` lines X–Y
- [Pattern 2] `path/file` lines X–Y

## Notes & Assumptions

- Impl decisions: [ ], [ ]
- Cross‑repo coord: [ ], [ ]
- Data model: [ ], [ ]
- Risks: [ ], [ ]
- Testing: integrated with each PR (avoid standalone)
- Assumptions: ✅[1], ✅[2], ❌[3 needs verify]
