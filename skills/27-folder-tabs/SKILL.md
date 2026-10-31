---
name: 27-folder-tabs
description: Use when a small set of sections should look like physical folders stacked front to back with only their top tabs showing, and choosing a tab pulls that folder to the front. Folder Tabs (檔案夾標籤頁) recipe built on accessible tab semantics with reduced-motion handling.
---
# 27 — 檔案夾標籤頁 / Folder Tabs

**Category:** 導覽與視圖 / Navigation & Views

## Effect

Several pages are stacked like folders in a binder: each sits slightly behind the last and only its coloured top tab peeks out. Choosing a tab slides that folder forward to the front while every other folder steps back one layer, so switching content feels like pulling a file out of a drawer rather than swapping text.

## When to use

Use for 3–5 sibling sections of one object: a trip binder (Plan, Stays, Views, Notes), a project page (Brief, Assets, Feedback), a product page (Details, Sizing, Care) or a profile. Each folder can have its own colour to help memory. Not for more than about 5 sections, or for navigation between unrelated pages. This skill is an interaction recipe, not an existing code component.

## Interaction contract

- Input: click or tap a tab; keyboard follows the WAI-ARIA tabs pattern: Tab moves into the tab list, Left/Right arrows move between tabs, Home/End jump to first/last, Enter/Space activates (or automatic activation on arrow, chosen consistently).
- States: each folder has a depth index; the active folder is depth 0 (front, full opacity, full height), the others are depth 1..n with a small vertical offset, slight scale-down or darkening, and lower `z-index`. Tabs stay visible at every depth.
- Transition: the chosen folder rises and comes forward; the previous front folder steps back exactly one layer; folders that were already behind it keep their relative order. Quick repeated choices interrupt cleanly from the current pose.
- Edge cases: long tab labels truncate with a tooltip or wrap to two lines; folders with very different content heights (container animates to the active folder's height or uses a fixed height with internal scroll); one tab only (render as a plain card); deep link to a tab (`?tab=notes` or a hash) opens that folder first.
- Accessibility: `role="tablist"`, `role="tab"` with `aria-selected` and `aria-controls`, `role="tabpanel"` with `aria-labelledby`; inactive panels are `hidden` or `inert` so only the front folder's content is focusable and read. Colour is never the only sign of the active tab (add weight, position or an indicator). Ensure tab text contrast on every folder colour.
- Reduced motion: switch the front folder instantly or with a short crossfade; keep the stacked look.

## Implementation notes

- Structure: one relative container; each folder is an absolutely positioned layer with its tab as a shaped top edge (an SVG path or a `clip-path` with rounded shoulders), and tabs are offset horizontally so all are visible.
- Depth: drive `transform: translateY(depth × 6–10px) scale(1 − depth × 0.02)`, `filter: brightness(1 − depth × 0.06)` and `z-index` from the depth index. Animate transform and filter; switch `z-index` at the start of the transition for the rising folder.
- Motion: the chosen folder can lift slightly (translateY negative) mid-way before settling, which sells the "pulling out" feeling. 300–450 ms with a spring.
- Framer Motion (`animate` on depth-derived values) or plain CSS transitions on custom properties both work; a small state machine holds the order array.
- Avoid: re-mounting content on every switch if it holds state (inputs, scroll position); keep panels mounted and hidden.

## Acceptance criteria

1. All tabs are visible at all times; the active folder is clearly in front and the others step back one layer each.
2. Switching animates smoothly and can be interrupted without glitches; relative order of background folders is preserved.
3. Full keyboard support per the WAI-ARIA tabs pattern; only the active panel is reachable and announced.
4. Active state is shown by more than colour and every tab meets contrast requirements.
5. Reduced-motion mode switches without sliding.
6. Responsive at 375px, 768px and 1440px; deep links open the correct tab.

## Copy-ready English prompt

```text
Create a reusable folder-tabs component. Stack 3 to 5 content panels front to back like folders in a binder, each with its own colour and a shaped top tab, with the tabs offset horizontally so every tab is always visible. The active folder sits in front at full brightness; each folder behind it is offset slightly lower, scaled down a little and darkened according to its depth. Selecting a tab by click, tap or keyboard pulls that folder to the front with a small lift, and every other folder steps back one layer while keeping its relative order. Drive the stack from a depth index and animate only transform, opacity and filter with a spring, interrupting cleanly on rapid changes. Implement the WAI-ARIA tabs pattern (tablist, tab with aria-selected and aria-controls, tabpanel, arrow keys, Home and End), keep inactive panels mounted but hidden from focus and screen readers, show the active tab by more than colour and keep text contrast on every folder colour. Support a deep link to a tab and animate the container height to the active panel. With prefers-reduced-motion, switch instantly. Expose sections, colours, labels, initial tab and activation mode as props.
```
