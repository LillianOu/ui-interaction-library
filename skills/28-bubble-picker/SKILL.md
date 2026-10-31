---
name: 28-bubble-picker
description: Use when an onboarding, preference or filter screen lets people pick several interests from a playful cluster of different-sized circles that grow and push their neighbours aside when chosen. Bubble Picker (圓泡堆疊選擇) multi-select recipe with keyboard, screen-reader and reduced-motion support.
---
# 28 — 圓泡堆疊選擇 / Bubble Picker

**Category:** 輸入與控制 / Inputs & Controls

## Effect

Options appear as a tightly packed cluster of circles of different sizes, like soap bubbles. Tapping one makes it swell and fill with the brand colour, with a small check mark; the bubbles around it are nudged outward, then the whole cluster settles back together around the new shape. Tapping it again shrinks it and the cluster closes up. Choosing interests becomes a small physical moment instead of a list of checkboxes.

## When to use

Use for onboarding ("What do you like?"), interest or topic selection, content filters, mood or tag pickers and lightweight surveys with about 6–20 options. Size can encode popularity or importance. Not for long or precise lists, ordered choices or anything requiring search; use a checkbox list or combobox there. This skill is an interaction recipe, not an existing code component.

## Interaction contract

- Input: click or tap a bubble to toggle; keyboard Tab to the group, arrow keys to move between bubbles (in reading order), Space or Enter to toggle. Optional drag to nudge bubbles is decorative only.
- States per bubble: **unselected** (translucent fill, outline), **selected** (larger radius, solid primary fill, check mark, white label), **disabled** (muted, not focusable or `aria-disabled`), **focused** (visible ring). Group states: empty, some selected, max reached (remaining bubbles disabled with a hint), error (for example "Pick at least 3").
- Feedback: a counter such as "3 picked" updates with each change; the continue button enables at the minimum.
- Edge cases: labels longer than the bubble (shrink text to a minimum size, then wrap or truncate with full name available), container resize (cluster re-centres), many options on a small screen (allow vertical scroll of the cluster area, never overlap labels), reload with saved selections.
- Accessibility: build it as a real multi-select: each bubble is a `<button aria-pressed>` or a visually styled checkbox in a `fieldset` with a `legend`. The bubble's position must not decide reading order; the DOM order is a sensible list order. Announce the counter in a polite live region. Colour is not the only selection signal (check mark plus size change). Touch targets stay at least 44px even for the smallest bubble.
- Reduced motion: toggle size and fill instantly, place bubbles in a static packed layout and skip the physics settling.

## Implementation notes

- Layout options:
  - **Physics:** d3-force with `forceCollide(radius + gap)`, `forceX/forceY` toward the centre and a gentle `forceManyBody`. On toggle, change the node's radius and reheat the simulation (`alpha(0.3).restart()`), so neighbours are pushed away and drift back. Stop the simulation when it cools to save battery.
  - **Static pack:** `d3.packSiblings` for an initial tight layout, then animate positions with springs on change. More predictable, less lively.
- Render as absolutely positioned buttons (DOM, better accessibility and text rendering) driven by simulation coordinates through `transform`, or SVG `<circle>` + `<foreignObject>`/`<text>` with matching buttons.
- Selected radius about 1.25–1.4× base; animate radius with a spring so it overshoots slightly.
- Clamp bubbles inside the container bounds with a boundary force so nothing drifts off screen.
- Avoid: running the simulation every frame forever, using canvas without an accessible DOM equivalent, letting a selected bubble cover another's label at rest.

## Acceptance criteria

1. Bubbles of different sizes start tightly packed with no overlaps and readable labels.
2. Toggling a bubble grows and fills it, pushes neighbours away, and the cluster settles without overlap within about one second.
3. Works with mouse, touch and keyboard; screen readers report each option's name and selected state and the running count.
4. Min and max selection rules, disabled options and saved selections work.
5. Reduced-motion mode toggles without physics; simulation stops when idle and is cleaned up on unmount.
6. Responsive at 375px, 768px and 1440px with 44px minimum targets.

## Copy-ready English prompt

```text
Create a reusable bubble picker for multi-select. Render options as circles of different sizes packed tightly in a cluster, each with a centred label, a translucent fill and a soft outline. Toggling a bubble by click, tap, Space or Enter makes it grow about 1.3 times, fill with the primary colour and show a check mark, while neighbouring bubbles are pushed outward and the whole cluster settles back together around the new size; toggling again shrinks it and the cluster closes up. Use d3-force with collision, centring and boundary forces, reheating the simulation on change and stopping it when it cools, and render the bubbles as real buttons with aria-pressed (or checkboxes in a fieldset with a legend) positioned by transform. Keep DOM order as a sensible reading order, support arrow-key movement between options, show a polite live counter such as "3 picked", support minimum and maximum selections with disabled states and a hint, and keep every target at least 44px. Fit long labels by shrinking then wrapping, keep everything inside the container and re-centre on resize. With prefers-reduced-motion, use a static packed layout and instant toggles. Expose options, sizes, selected values, min, max and colours as props, with an onChange callback.
```
