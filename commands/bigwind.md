Here’s the requested concise version wrapped in triple quotes:

# Big Wins Command

## Description

Suggest **up to 3 high-impact improvements** (1–4 weeks each) across the **entire workspace** unless a scope is specified.

## Trigger

User asks for "big wins" or strategic improvements.

## Steps

1.  **Identify Initiatives**: Look for architecture upgrades, performance boosts, developer experience improvements, security hardening, or major feature enablement.
2.  **Present Options**: For each option, provide:
    - **Initiative:** Short description.
    - **Why Now:** Impact rationale.
    - **Scope & Milestones:** Key phases.
    - **Snippet:** Minimal illustrative code/config (if relevant).
    - **Risks / Mitigations:** Brief.
3.  **Recommend**: Provide **1 clear recommendation** optimized for impact vs. effort and low risk.
4.  **Wait**: Stop after presenting and wait for user choice. Do not apply changes automatically.

## Output Format

Markdown list of options, followed by a recommendation.

## Example (Optional)

**Option 1: Add Request Coalescing (perf)**

- **Initiative:** Collapse duplicate concurrent fetches.
- **Why Now:** Reduce p95 latency and origin load.
- **Scope & Milestones:** Week 1: singleflight; Week 2: soft cache; Week 3: rollout.
- **Snippet:**

```ts
if (inflight.has(id)) return inflight.get(id)!;
```

- **Risks / Mitigations:** TTL tuning to avoid herd effect.
