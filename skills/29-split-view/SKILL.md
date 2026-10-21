---
name: 29-split-view
description: Use when a page has two stacked panes (for example a map or hero above and a list below) and people should drag a horizontal handle to resize them, with content re-laying out and the divider snapping to one of three set ratios. Split View (拖動分屏比例) recipe with keyboard, touch and reduced-motion handling.
---
# 29 — 拖動分屏比例 / Split View

**Category:** 排版互動 / Layout Relationships

## Effect

The screen is split into a top pane and a bottom pane with a horizontal grab handle between them. Dragging the handle resizes both panes live; as space changes, the content in each pane rearranges itself (for example the bottom list shows compact horizontal chips when short, and full rows with thumbnails when tall). Letting go snaps the divider to the nearest of three preset ratios, so the layout always lands somewhere designed.

## When to use

Use for map + results, media + details, route overview + stops, chart + table, editor + preview or chat + context screens, where people want to trade space between two related views. Three snap points (for example 25 / 50 / 75% top height) usually cover "focus top", "balanced" and "focus bottom". For a sheet that slides over content rather than resizing two panes, use 07 Drag to Expand & Collapse. This skill is an interaction recipe, not an existing code component.

## Interaction contract

- Input: pointer drag on the handle (mouse, touch, pen) using Pointer Events with pointer capture; tap or click the handle to cycle snap points; keyboard focus on the handle with Up/Down arrows moving to the previous/next snap point (or small steps with Shift), Home/End for the extremes.
- States: **resting at snap A/B/C**, **dragging** (divider follows the finger 1:1 within min and max limits, with rubber-band resistance past them), **snapping** (spring to the target chosen by position and release velocity), **re-laying out** (each pane switches content layout at defined height thresholds).
- Snap choice: project the release position with velocity (a quick flick goes to the next snap in that direction) and clamp to the nearest snap point.
- Edge cases: pointer cancel or leaving the window ends the drag and snaps; orientation change and on-screen keyboard keep the current snap ratio, not the pixel height; content inside a pane scrolls independently and must not start a divider drag; very small screens may drop to two snap points.
- Accessibility: the handle is a focusable element with `role="separator"`, `aria-orientation="horizontal"`, `aria-valuenow`/`aria-valuemin`/`aria-valuemax` (percentage) and `aria-valuetext` such as "Map 50%, list 50%", plus an accessible name. Provide a visible handle with at least a 44px hit area. Content layout changes must not move keyboard focus.
- Reduced motion: jump to the chosen snap point without the spring and swap pane layouts without transition.

## Implementation notes

- Layout: a column grid `grid-template-rows: var(--top) auto 1fr` where `--top` is the divider position; during drag, update the custom property in a `requestAnimationFrame` callback, not on every pointer event.
- For heavy panes (maps, video), consider transforming during drag and committing the real size on release, or throttling resize events into the pane.
- Content re-layout: use container queries (`@container (min-height: …)`) on each pane so their content adapts to the pane size without JavaScript; e.g. the list switches from a horizontal chip row to vertical rows with thumbnails and subtitles.
- Snap physics: spring with mild overshoot (stiffness ~300, damping ~30) or GSAP with an ease-out-back; Framer Motion `drag="y"` with `dragConstraints` and `dragElastic` also works.
- Remember the last snap point per user if it helps (localStorage with try/catch).
- Avoid: `touch-action` that blocks page scroll everywhere (set `touch-action: none` only on the handle), resizing via `height` transitions on every frame.

## Acceptance criteria

1. Dragging the handle resizes both panes live and smoothly, within limits, with resistance past them.
2. Release snaps to one of three ratios, chosen by position and velocity; tap cycles snaps.
3. Pane content switches between compact and full layouts at defined sizes without flicker or focus loss.
4. Keyboard and screen-reader users can change the split through the separator role and value attributes.
5. Pointer cancel, rotation, keyboard appearance and nested scrolling are handled; listeners are cleaned up.
6. Reduced-motion mode snaps without animation. Responsive at 375px, 768px and 1440px.

## Copy-ready English prompt

```text
Create a reusable vertical split view with a draggable divider. Show a top pane (for example a hero image or map with a title) and a bottom pane (for example a list of places with thumbnails), separated by a visible horizontal grab handle with at least a 44px hit area. Dragging the handle with Pointer Events and pointer capture resizes both panes live, clamped between minimum and maximum heights with rubber-band resistance beyond them. On release, snap to the nearest of three preset ratios (for example 25, 50 and 75 percent) using both position and release velocity, with a gentle spring. Tapping the handle cycles the snap points. Use container queries so each pane re-lays out its content by available height: the list shows compact horizontal chips when short and full rows with thumbnails when tall. Give the handle role="separator" with aria-orientation, aria-valuenow, min, max and a readable aria-valuetext, and support Up and Down arrows, Home and End. Handle pointer cancel, rotation and the on-screen keyboard by keeping the current ratio, keep nested pane scrolling independent from the divider, and update size in requestAnimationFrame. With prefers-reduced-motion, jump to the snap point without a spring. Expose snap ratios, limits, initial ratio and the two pane contents as props.
```
