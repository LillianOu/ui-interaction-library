---
name: 24-expanding-grid
description: Use when a dashboard or bento grid of cards should let one card grow to full width in place while the others reflow beneath it, instead of opening a new page. Expanding Grid (點一格撐成通欄) recipe with keyboard, focus and reduced-motion handling.
---
# 24 — 點一格撐成通欄 / Expanding Grid

**Category:** 網格與面板 / Grids & Panels

## Effect

A two-column grid of cards with different heights (a stat, a photo, the weather, notes). Tapping any card makes it stretch across the full row and grow taller to show more detail, while the cards after it slide down and repack into the columns. Tapping it again returns everything to the original arrangement. The user never leaves the page, so the context stays visible around the detail.

## When to use

Use for daily overviews, trip planners, KPI or dashboard tiles, galleries with captions and settings summaries, where each tile has a short and a long form. Not for content that needs its own URL, long reading or a form; use 01 Shared Element Expansion or a real route for that. This skill is an interaction recipe, not an existing code component.

## Interaction contract

- Input: click or tap anywhere on the card (or on an explicit expand icon); Enter or Space when the card's toggle is focused; Escape collapses the open card.
- States: **collapsed grid**, **expanding**, **one card expanded** (spans all columns, taller, extra content revealed), **collapsing**. Default to one expanded card at a time; opening another collapses the first in the same transition.
- Reflow: cards after the expanded one move down in reading order; the cards before it do not move. Keep the order stable; never shuffle cards to fill gaps in a way that changes their sequence.
- Scrolling: after expanding, make sure the expanded card's top is in view (gentle `scrollIntoView({ block: 'nearest' })`), without yanking the page.
- Edge cases: an odd number of cards, a card at the end of the grid, rapid repeated taps (reverse from current state), content that loads late inside the expanded card, resize across the breakpoint where the grid becomes one column (expansion then only changes height).
- Accessibility: each card has a toggle button with `aria-expanded` and `aria-controls` pointing at its detail region. The extra content is hidden from assistive tech when collapsed. Focus stays on the toggle; reading order follows DOM order.
- Reduced motion: change layout instantly or with a short fade; no sliding.

## Implementation notes

- Layout: CSS Grid with `grid-template-columns: repeat(2, 1fr)`, `grid-auto-flow: row dense` only if reordering is acceptable (usually it is not; prefer plain `row`). The expanded card gets `grid-column: 1 / -1` and a larger row span or auto height.
- Animation: FLIP all cards. Record every card's rect, apply the new class, record again, then animate each card's `transform` (and `scale` for the one changing size, with counter-scaled inner content to avoid stretched text). Framer Motion `layout` + `LayoutGroup`, GSAP Flip plugin or the View Transitions API all handle this well.
- Reveal the extra content after the card has mostly grown (stagger 80–120 ms) and hide it first on collapse, so text never squeezes.
- Keep the card's identity visible during the change (same colour, title and key number) so the eye can follow it.
- Duration around 400–550 ms with a spring or ease-in-out; cards further from the expanded one can lag slightly for a natural ripple.
- Avoid: animating `grid-template-rows` or `height: auto` directly on many items, nested scroll areas inside the expanded card on mobile.

## Acceptance criteria

1. Any card can expand to the full row and the remaining cards reflow below it in their original order.
2. Every card moves smoothly to its new position; no card teleports or overlaps another at rest.
3. Escape and a second tap collapse it; opening a different card closes the current one in one motion.
4. `aria-expanded` is correct, hidden detail is not focusable, focus never jumps.
5. Reduced-motion mode switches layouts without movement.
6. Responsive at 375px (single column), 768px and 1440px; no layout shift outside the grid.

## Copy-ready English prompt

```text
Create a reusable expanding grid. Show a two-column grid of cards with different heights, for example a stat tile, two photo tiles, a weather tile and a notes tile. Each card has a toggle button with aria-expanded and aria-controls. Activating a card by click, tap, Enter or Space makes it span the full row and grow taller to reveal extra detail, while the cards after it smoothly slide down and repack in their original order; the cards before it stay put. A second activation or Escape restores the original grid, and opening another card collapses the current one in the same transition. Use a FLIP animation (Framer Motion layout, GSAP Flip or View Transitions) so cards animate only transform and opacity, counter-scale inner content so text never stretches, and reveal extra content after the card has grown and hide it before it shrinks. Reverse from the current state on rapid taps, keep the expanded card in view without jarring scroll, and collapse to a single column below 600px where expansion only adds height. With prefers-reduced-motion, change layout instantly. Expose the card data, column count, one-or-many expansion mode and easing as props.
```
