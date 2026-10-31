---
name: 60-shimmer
description: Use when content is loading and should show a skeleton with a light band sweeping across it, or when a promo button needs an occasional sheen. Shimmer (流光) recipe with skeleton layout, aria-busy, timing and reduced-motion handling.
---
# 60 — 流光 / Shimmer

**Category:** 回饋與載入 / Feedback & Loading

## Effect

A soft band of light sweeps across grey placeholder shapes while content loads, telling people something is on its way and roughly what it will look like. On a promo button, an occasional sheen catches the eye.

## When to use

Use for loading states of cards, lists, profiles and feeds where the layout is known in advance, and sparingly as a sheen on one promotional button. Not for loads under ~300ms (show nothing, to avoid flicker), unknown layouts, or as a permanent decoration on many elements. This skill is an interaction recipe, not an existing code component.

Part of the sixteen-effect motion set (45–60), inspired by the Douyin video 「非程序员AI开发必看教程：16种常见动画效果科普」 by 大锤和AI. Specs, prompts and demo are written for this library. Timing and easing follow 45 Easing & Timing.

## Interaction contract

- Input: loading state from data; the button sheen runs on a slow timer and on hover/focus.
- States: loading (skeleton + shimmer), loaded (real content replaces skeleton), error (skeleton replaced by a message and retry), slow (after ~10s, add a text status).
- Cancellation and edge cases: show the skeleton only if loading takes longer than ~300ms; skeleton shapes match the real layout so nothing jumps when content arrives; stops when off screen.
- Accessibility: the loading region has `aria-busy="true"` and a visually hidden 'Loading…' label; set `aria-busy="false"` when done. Skeleton shapes are `aria-hidden`.
- Reduced motion: static skeleton (or a slow opacity pulse); no sheen on the button.

## Implementation notes

- Skeleton blocks: `background: linear-gradient(90deg, base 0%, highlight 40%, base 80%); background-size: 250% 100%; animation: shimmer 1.4s linear infinite` moving `background-position` from 100% to -150%.
- Use one shared gradient (`background-attachment: fixed` on the blocks, or one overlay) so all blocks shimmer in sync.
- Button sheen: `::after` with a diagonal white gradient translating from -120% to 120%, running every ~3s and once on hover.
- Fade real content in over ~200ms when it arrives.
- Avoid: skeletons that don't match the final layout, shimmer on fast loads, and sheens on several buttons.

## Acceptance criteria

1. The skeleton matches the real layout and shimmers at ~1.4s per pass; content replaces it without a jump.
2. `aria-busy` is true while loading and false after; the skeleton is hidden from screen readers.
3. No skeleton flashes for loads under ~300ms.
4. Works with mouse, touch and keyboard as described in the interaction contract.
5. Reduced-motion mode presents the same information without the movement described above.
6. Only `transform`, `opacity`, `filter`, colour and shadow animate; no layout thrash; smooth on a mid-range phone.
7. No console errors or leaks; listeners, observers, timers and animation frames are cleaned up.
8. Responsive at 375px, 768px and 1440px.

## Prompt terms

| English prompt line | 中文提示詞 |
| --- | --- |
| Show a Shimmer skeleton while the card loads, and add an occasional Shimmer sheen across the promo button. | 卡片載入時顯示帶流光（Shimmer）的骨架屏，促銷按鈕偶爾掃過一道流光。 |

## Copy-ready English prompt

```text
Add shimmer loading states. While data loads (only if it takes more than 300ms), render a skeleton that matches the real card layout: grey blocks with linear-gradient(90deg, base, highlight 40%, base 80%), background-size 250%, animating background-position 100% → -150% over 1.4s linear infinite, all blocks in sync. The region has aria-busy=true and a visually hidden 'Loading…'; set aria-busy=false and fade the real content in over 200ms when ready; show a message and Retry on error. Add a diagonal sheen ::after on the promo button that sweeps every 3s and once on hover/focus. Under prefers-reduced-motion, static skeleton and no sheen.
```
