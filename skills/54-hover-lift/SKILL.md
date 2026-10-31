---
name: 54-hover-lift
description: Use when product cards, tiles or clickable list items should rise slightly with a deeper shadow on hover or focus, and settle when pressed. Hover Lift (懸停上浮) recipe with timing, touch, keyboard and reduced-motion handling.
---
# 54 — 懸停上浮 / Hover Lift

**Category:** 游標與懸停 / Cursor & Hover

## Effect

The card rises a few pixels and its shadow grows as the pointer moves onto it, showing that it is clickable and which one you are on. Pressing settles it back down slightly, like pushing a real card.

## When to use

Use for product cards, article cards, dashboard tiles and any clickable surface in a grid. Pair with 51 Spotlight only on dark designs. Not for non-clickable cards (lift promises an action). This skill is an interaction recipe, not an existing code component.

Part of the sixteen-effect motion set (45–60), inspired by the Douyin video 「非程序员AI开发必看教程：16种常见动画效果科普」 by 大锤和AI. Specs, prompts and demo are written for this library. Timing and easing follow 45 Easing & Timing.

## Interaction contract

- Input: hover with a fine pointer, keyboard focus (`:focus-visible`), touch press (`:active`).
- States: resting, lifted (hover/focus), pressed, disabled (no lift).
- Cancellation and edge cases: moving quickly across a grid lifts and drops cards smoothly without flicker; lifted cards don't overlap or clip neighbours (leave gap and avoid `overflow: hidden` on the grid).
- Accessibility: the whole card is one link or button with a clear accessible name; focus shows lift plus a visible focus ring.
- Reduced motion: no rise; the shadow or border change alone shows the state.

## Implementation notes

- `transform: translateY(-6px)` and a deeper `box-shadow` on `:hover, :focus-visible`; `translateY(-2px)` on `:active` with a ~100ms transition.
- Durations 150–200ms ease-out in, slightly faster out.
- For smoother shadows on many cards, animate the opacity of a pre-rendered shadow layer (`::after`) instead of `box-shadow`.
- Wrap hover styles in `@media (hover: hover)` so touch devices don't get stuck lifted.
- Avoid: lifts over 10px, scaling text, and lifting non-interactive cards.

## Acceptance criteria

1. Cards rise 4–8px with a deeper shadow in 150–200ms on hover and focus, and settle on press.
2. Touch devices never get stuck in the hover state.
3. Lifted cards are not clipped by their container.
4. Works with mouse, touch and keyboard as described in the interaction contract.
5. Reduced-motion mode presents the same information without the movement described above.
6. Only `transform`, `opacity`, `filter`, colour and shadow animate; no layout thrash; smooth on a mid-range phone.
7. No console errors or leaks; listeners, observers, timers and animation frames are cleaned up.
8. Responsive at 375px, 768px and 1440px.

## Prompt terms

| English prompt line | 中文提示詞 |
| --- | --- |
| Add Hover Lift to the product cards: on hover or focus the card rises 6px and its shadow deepens in 180ms; pressing settles it back. | 商品卡片加懸停上浮（Hover Lift）：滑鼠移上或聚焦時上浮 6px、陰影加深，180 毫秒；按下時回落。 |

## Copy-ready English prompt

```text
Add a hover lift to these cards. Each card is a single link or button. Under @media (hover: hover), :hover and :focus-visible apply translateY(-6px) and a deeper shadow over 180ms cubic-bezier(.2,.8,.2,1); :active uses translateY(-2px) with a 100ms transition. Keep a visible focus ring. Make sure the grid doesn't clip lifted cards. For many cards, animate the opacity of a pre-rendered shadow layer instead of box-shadow. Under prefers-reduced-motion, change shadow or border only, with no rise.
```
