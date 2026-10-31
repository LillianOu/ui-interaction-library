---
name: 51-spotlight
description: Use when a grid of feature or pricing cards on a dark or tinted page should feel alive, with a soft glow following the cursor inside each card and lighting its border. Spotlight (聚光) recipe with pointer tracking, keyboard focus, touch and reduced-motion handling.
---
# 51 — 聚光 / Spotlight

**Category:** 游標與懸停 / Cursor & Hover

## Effect

As the cursor moves over a group of cards, a soft radial glow follows it inside each card and lights up the part of the border nearest the cursor, even spilling onto neighbouring cards. It shows where you are and makes a static grid feel responsive.

## When to use

Use for feature grids, pricing cards and bento layouts, usually on dark backgrounds where light reads well. Not on light, busy backgrounds where the glow disappears, or on long lists. This skill is an interaction recipe, not an existing code component.

Part of the sixteen-effect motion set (45–60), inspired by the Douyin video 「非程序员AI开发必看教程：16种常见动画效果科普」 by 大锤和AI. Specs, prompts and demo are written for this library. Timing and easing follow 45 Easing & Timing.

## Interaction contract

- Input: pointer move over the group; keyboard focus places the glow at the centre of the focused card; on touch, the glow follows a drag or appears where the finger presses.
- States: idle (no glow), hovering (glow at pointer), focused (glow centred), pressed.
- Cancellation and edge cases: pointer leave fades the glow out; resize and scroll keep positions correct (measure on each move, not once).
- Accessibility: cards are links or buttons with visible focus styles independent of the glow; glow never lowers text contrast below 4.5:1.
- Reduced motion: glow appears statically on hover or focus without following the pointer.

## Implementation notes

- One `pointermove` listener on the group; for each card write `--x` and `--y` = pointer position minus card's `getBoundingClientRect()`. Update inside `requestAnimationFrame` if many cards.
- Glow: card `::before` with `radial-gradient(220px circle at var(--x) var(--y), rgba(accent,.2), transparent 60%)`; border light: `::after` with the same gradient, masked to a 1px ring via `mask-composite: exclude`.
- Fade the glow with opacity (300ms ease-out), not by changing the gradient.
- Avoid: per-card listeners that only light the hovered card (the effect is better when neighbours catch light), large blur filters, and glow on light backgrounds without enough contrast.

## Acceptance criteria

1. Glow follows the pointer smoothly within each card and lights the nearest border.
2. Keyboard focus shows the glow centred on the focused card; touch shows it on press.
3. Text contrast stays at 4.5:1 or better under the glow.
4. Works with mouse, touch and keyboard as described in the interaction contract.
5. Reduced-motion mode presents the same information without the movement described above.
6. Only `transform`, `opacity`, `filter`, colour and shadow animate; no layout thrash; smooth on a mid-range phone.
7. No console errors or leaks; listeners, observers, timers and animation frames are cleaned up.
8. Responsive at 375px, 768px and 1440px.

## Prompt terms

| English prompt line | 中文提示詞 |
| --- | --- |
| Add a Spotlight to the feature cards: a soft radial glow follows the cursor inside each card and lights the nearest border; on keyboard focus the glow sits in the centre. | 功能卡片加聚光效果（Spotlight）：滑鼠在卡片上移動時，柔和光暈跟隨游標並照亮附近邊框；鍵盤聚焦時光暈置中。 |

## Copy-ready English prompt

```text
Add a spotlight effect to this card grid. One pointermove listener on the grid sets --x and --y on every card (pointer position relative to each card's bounding rect). Each card has a ::before radial-gradient(220px circle at var(--x) var(--y), accent at 20% alpha, transparent 60%) and a ::after border ring using the same gradient masked to 1px with mask-composite: exclude. The glow fades in on grid hover (300ms ease-out) and out on leave. On keyboard focus, centre the glow on that card; on touch, follow the drag. Keep text contrast at 4.5:1. Under prefers-reduced-motion, show a static glow on hover/focus.
```
