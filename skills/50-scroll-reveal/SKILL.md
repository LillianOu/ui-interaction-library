---
name: 50-scroll-reveal
description: Use when lists, articles, feature blocks or cards should fade and rise into place as they scroll into view, once. Scroll Reveal (滾動出現) recipe with thresholds, progressive enhancement and reduced-motion handling.
---
# 50 — 滾動出現 / Scroll Reveal

**Category:** 滾動動效 / Scroll

## Effect

Each block fades in and rises a short distance as it enters the screen, so the page seems to assemble itself as you read. It plays once per block.

## When to use

Use on landing pages, blogs, feature lists and portfolios. Pair with 47 Stagger for groups. Don't use it on content above the fold that should be visible immediately, or on data tables and app screens people return to often. This skill is an interaction recipe, not an existing code component.

Part of the sixteen-effect motion set (45–60), inspired by the Douyin video 「非程序员AI开发必看教程：16种常见动画效果科普」 by 大锤和AI. Specs, prompts and demo are written for this library. Timing and easing follow 45 Easing & Timing.

## Interaction contract

- Input: the block entering the viewport (or a scroll container) by any scroll method, including keyboard focus scrolling to it.
- States: waiting (hidden, offset), revealed. Once revealed it stays revealed.
- Cancellation and edge cases: content above the fold on load is shown without animation or reveals immediately; jumping to an anchor reveals the target at once; printing shows everything.
- Accessibility: content is readable if JavaScript fails: start visible and only add the hidden state once the script has run (`.js` class on the root). Focusing an unrevealed block reveals it.
- Reduced motion: everything visible, no movement.

## Implementation notes

- `IntersectionObserver` with threshold ~0.15–0.2 (or rootMargin `0px 0px -10% 0px`); add an `.in` class, then `unobserve` the element.
- Hidden state: `opacity: 0; transform: translateY(20px)`; revealed: `opacity: 1; transform: none`; 400–600ms ease-out.
- CSS-only alternative: `animation-timeline: view()` with `animation-range: entry`.
- Avoid: revealing on every scroll up and down, large distances (over 40px), slow durations, and hiding content from users without JavaScript.

## Acceptance criteria

1. Blocks fade and rise 16–24px once, 400–600ms ease-out, as they enter.
2. Content is visible without JavaScript and on print; above-the-fold content isn't delayed.
3. Keyboard focus and anchor jumps reveal their target immediately.
4. Works with mouse, touch and keyboard as described in the interaction contract.
5. Reduced-motion mode presents the same information without the movement described above.
6. Only `transform`, `opacity`, `filter`, colour and shadow animate; no layout thrash; smooth on a mid-range phone.
7. No console errors or leaks; listeners, observers, timers and animation frames are cleaned up.
8. Responsive at 375px, 768px and 1440px.

## Prompt terms

| English prompt line | 中文提示詞 |
| --- | --- |
| Add Scroll Reveal to the article list: each card fades in and rises 20px as it enters the viewport, once only. | 文章列表加滾動出現（Scroll Reveal）：每張卡片進入視窗時淡入並上移 20px，只播一次。 |

## Copy-ready English prompt

```text
Add scroll reveal to these blocks. Add a .js class to <html> when the script runs; only under .js do blocks start at opacity 0 and translateY(20px). An IntersectionObserver (threshold 0.2) adds .in when a block enters, transitioning to opacity 1 and no transform over 500ms cubic-bezier(.2,.8,.2,1), then unobserves it. Blocks already in view on load show immediately. Focus or an anchor jump reveals the target at once. Combine with a 60ms stagger for groups. Under prefers-reduced-motion everything is visible from the start.
```
