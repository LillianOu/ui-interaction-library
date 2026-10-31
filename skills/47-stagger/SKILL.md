---
name: 47-stagger
description: Use when a group of cards, list items, menu entries or grid tiles appears at once and should enter one after another instead of all together. Stagger (錯峰) recipe with step timing, caps, keyboard and reduced-motion handling.
---
# 47 — 錯峰 / Stagger

**Category:** 動效基礎 / Motion Foundations

## Effect

Items in a group start their entrance one after another, a few tens of milliseconds apart, so the eye reads the group in order instead of seeing one block pop in. The whole sequence is still short.

## When to use

Use for grid and list entrances, opening menus, search results arriving, dashboard cards loading. Combine with 50 Scroll Reveal for lists that enter as you scroll. Don't stagger content people are waiting to read immediately, like an updated table. This skill is an interaction recipe, not an existing code component.

Part of the sixteen-effect motion set (45–60), inspired by the Douyin video 「非程序员AI开发必看教程：16种常见动画效果科普」 by 大锤和AI. Specs, prompts and demo are written for this library. Timing and easing follow 45 Easing & Timing.

## Interaction contract

- Input: triggered by the group entering (mount, data loaded, menu opened, scrolled into view).
- States: hidden, entering (staggered), shown. Exit is usually all at once and faster, or in reverse order for menus.
- Cancellation and edge cases: cap the total so long lists don't take seconds; items after the cap (about 8–10) enter together. Re-triggering resets cleanly. Items added later enter on their own without replaying the group.
- Accessibility: items are in the DOM and readable before they finish animating; focus can move to an item that is still animating.
- Reduced motion: all items appear at once, with no stagger or movement.

## Implementation notes

- Step 40–80ms; keep the whole sequence under ~500ms (so step × count ≤ 500ms, or cap the index).
- CSS: give each item `--i` and use `transition-delay: calc(min(var(--i), 8) * 60ms)`; each item fades and rises 8–16px with ease-out, 300–450ms.
- JS: GSAP `stagger`, Motion `stagger()`, or Framer Motion `staggerChildren`.
- Order follows reading order (left to right, top to bottom); for grids, a diagonal order (row + column) also reads well.
- Avoid: steps over 100ms, staggering exits slowly, and replaying the stagger on every re-render.

## Acceptance criteria

1. Items start 40–80ms apart in reading order, and the whole sequence finishes within ~500ms plus one item's duration.
2. Long lists are capped; later items don't wait seconds.
3. Content is readable and focusable before animation ends.
4. Reduced-motion mode presents the same information without the movement described above.
5. Only `transform`, `opacity`, `filter`, colour and shadow animate; no layout thrash; smooth on a mid-range phone.
6. No console errors or leaks; listeners, observers, timers and animation frames are cleaned up.
7. Responsive at 375px, 768px and 1440px.

## Prompt terms

| English prompt line | 中文提示詞 |
| --- | --- |
| Stagger the grid entrance: cards appear one after another 60ms apart instead of all at once, each fading in and rising 12px; cap it so the whole sequence takes under half a second. | 網格入場用錯峰（Stagger）：卡片間隔 60 毫秒依次出現，每張淡入並上移 12px，不要同時出現；總時長控制在半秒內。 |

## Copy-ready English prompt

```text
Add a staggered entrance to this group of items. Each item fades in and rises 12px over 400ms with ease-out cubic-bezier(.2,.8,.2,1); item n starts at min(n, 8) × 60ms, so the sequence stays under ~500ms and later items enter together. Use a --i custom property and transition-delay (or the animation library already in the project). Trigger on mount or when the group scrolls into view, once. Exits happen together and faster. Items are in the DOM and focusable from the start. Under prefers-reduced-motion, show all items at once with no movement.
```
