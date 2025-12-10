# filetree-virtualization-v1

## Goal

Integrate @humanspeak/svelte-virtual-list into FileTree.svelte to virtualize the rendering of file nodes, improving performance for large directory structures by reducing DOM elements.

## Scope

- **In Scope:** Modify FileTree.svelte to use SvelteVirtualList for rendering processedNodes, handle item rendering for folders and files, maintain recursive behavior for children.
- **Out of Scope:** Changes to Tauri backend, data loading, other components, or full tree virtualization (focus on top-level).

## Risks

- Recursive rendering may not fully benefit from top-level virtualization: Mitigation - test with deep trees and consider recursive virtualization if needed.
- Accessibility issues with virtual scrolling: Mitigation - ensure keyboard navigation and screen reader support.
- Package compatibility with Svelte 5: Mitigation - verify in dev environment.

## Dependencies

- @humanspeak/svelte-virtual-list package installed.

## Priority

High

## Logging / Observability

- Add console logs for virtual list performance metrics (e.g., rendered items count).

## Implementation Plan (TODOs)

- [x] **Step 1: Install Package**
    - [x] Add @humanspeak/svelte-virtual-list to package.json in zinc project. (Already present)
    - [x] Run package manager to install. (Already installed)

- [x] **Step 2: Import and Setup**
    - [x] Import SvelteVirtualList in FileTree.svelte.
    - [x] Replace the {#each} block with SvelteVirtualList component.
    - [x] Configure props: items={processedNodes}, height for container.

- [x] **Step 3: Adapt Rendering**
    - [x] Use #snippet renderItem to render folder/file logic.
    - [x] Ensure recursive Self component works within snippet.
    - [x] Handle key prop for each item (use node.path).

- [ ] **Step 4: Test and Refine**
    - [ ] Test with small folder: verify rendering and interaction.
    - [ ] Test with large folder: check performance improvement.
    - [ ] Fix any issues with scrolling, expansion, or selection.

## Docs

- [x] Update FileTree.svelte comments to note virtualization.

## Testing

- [ ] Manual testing: Open large folder, measure render time and DOM elements. (Requires runtime testing)
- [ ] Unit tests: Ensure component props and events work. (No existing unit tests to run)

## Acceptance

- [ ] FileTree renders large directories without performance degradation.
- [ ] No regressions in functionality (expansion, selection, keyboard nav).
- [ ] DOM elements reduced significantly for large lists.

## Fallback Plan

If virtualization causes issues (e.g., broken recursion), revert to original {#each} implementation and explore alternative libraries like TanStack Virtual.

## References

- @humanspeak/svelte-virtual-list docs: https://github.com/humanspeak/svelte-virtual-list
- FileTree component: zinc/crates/ide/src/lib/components/organisms/FileTree/FileTree.svelte

## Complexity Check

- TODO Count: 12
- Depth: 2
- Cross-deps: 0
- **Decision:** Proceed (fits single PR)
