---
name: 49-parallax
description: Use when a hero or illustrated section has layered art (sky, mountains, foreground) and should gain depth as the page scrolls, with background layers moving slower than the foreground. Parallax (視差滾動) recipe with layer speeds, performance, mobile and reduced-motion handling.
---
# 49 — 視差滾動 / Parallax

**Category:** 滾動動效 / Scroll

## Effect

As the page scrolls, layers in the hero move at different speeds: the far background barely moves, the middle layers drift, and the foreground scrolls normally. The flat picture suddenly has depth.

## When to use

Use for landing page heroes, story pages and illustrated sections built from separate layers. Keep it subtle. Avoid it on dashboards, forms and content people need to read while scrolling. This skill is an interaction recipe, not an existing code component.

Part of the sixteen-effect motion set (45–60), inspired by the Douyin video 「非程序员AI开发必看教程：16种常见动画效果科普」 by 大锤和AI. Specs, prompts and demo are written for this library. Timing and easing follow 45 Easing & Timing.

## Interaction contract

- Input: page or container scroll by any method; optionally pointer position for a small horizontal shift on desktop.
- States: idle and scrolling; layers are positioned purely from scroll position, so scrolling back restores them exactly.
- Cancellation and edge cases: works when the page loads already scrolled; recalculates on resize; layers never reveal empty gaps (oversize back layers by the maximum offset).
- Accessibility: layers are decorative (`aria-hidden`); headline text inside the scene stays real text with enough contrast at every scroll position.
- Mobile: reduce speeds or disable on small screens if it stutters.
- Reduced motion: all layers stay still.

## Implementation notes

- Speed factors 0.1–0.6 for back layers (offset = scrollY × factor), 0 for the foreground. Total drift under ~150px.
- One `requestAnimationFrame`-throttled scroll listener writing `transform: translate3d(0, y, 0)` per layer, or CSS scroll-driven animations (`animation-timeline: scroll()` / `view()`).
- Add `will-change: transform` only to the moving layers. Use SVG or optimised images; set the hero to `overflow: hidden`.
- Avoid: `background-attachment: fixed` (janky on mobile), animating `background-position` or `top`, and big parallax on text people are reading.

## Acceptance criteria

1. Layers move at visibly different speeds, background slowest, without gaps at the edges.
2. Scroll position fully determines layer positions; reloading mid-page looks correct.
3. Text in the scene stays readable at every scroll position.
4. Works with mouse, touch and keyboard as described in the interaction contract.
5. Reduced-motion mode presents the same information without the movement described above.
6. Only `transform`, `opacity`, `filter`, colour and shadow animate; no layout thrash; smooth on a mid-range phone.
7. No console errors or leaks; listeners, observers, timers and animation frames are cleaned up.
8. Responsive at 375px, 768px and 1440px.

## Prompt terms

| English prompt line | 中文提示詞 |
| --- | --- |
| Add Parallax to the hero: sky, far mountains and near trees move at different speeds as the page scrolls, background slowest. | 首屏加視差滾動（Parallax）：天空、遠山、近樹隨頁面滾動以不同速度移動，背景最慢。 |

## Copy-ready English prompt

```text
Add a parallax hero. Build it from separate layers (sky, far mountains, title, near trees) inside an overflow-hidden section. On scroll, in one requestAnimationFrame-throttled handler, set each layer's transform: translate3d(0, scrollY × factor, 0) with factors sky 0.15, far mountains 0.3, title 0.5 (also fading out), foreground 0. Oversize back layers so no gaps show. Layers are aria-hidden; the title is real text. Disable or soften below 768px if needed. Under prefers-reduced-motion, keep every layer still. No background-attachment: fixed.
```
