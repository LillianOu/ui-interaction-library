---
name: 57-count-up
description: Use when stats, KPIs, dashboard figures or social-proof numbers should count up from zero to their value as they come into view. Count Up (數字滾動) recipe with easing, number formatting, screen readers and reduced-motion handling.
---
# 57 — 數字滾動 / Count Up

**Category:** 文字動效 / Text & Type

## Effect

Numbers run quickly from zero to their final value as they appear, slowing down as they land, so a stat feels earned and draws the eye.

## When to use

Use for landing page stats, dashboard KPIs, results sections and pricing savings. Not for numbers that update constantly (live data: animate the change instead, briefly) or for precise figures people compare side by side. This skill is an interaction recipe, not an existing code component.

Part of the sixteen-effect motion set (45–60), inspired by the Douyin video 「非程序员AI开发必看教程：16种常见动画效果科普」 by 大锤和AI. Specs, prompts and demo are written for this library. Timing and easing follow 45 Easing & Timing.

## Interaction contract

- Input: plays once when the number scrolls into view; an optional replay.
- States: waiting (0 or the final value if JS fails), counting, done.
- Cancellation and edge cases: works for integers, decimals, percentages, currencies and suffixes like + or k; negative values count from 0 down; the width doesn't jump as digits change; leaving the viewport mid-count finishes it.
- Accessibility: screen readers get the final value (visually hidden text or `aria-label`), not the counting values; don't use `aria-live` on the counting element.
- Reduced motion: final value shown immediately.

## Implementation notes

- `requestAnimationFrame` loop over 1–1.6s with ease-out-expo (`1 - 2^(-10t)`) so it slows near the end.
- Format with `Intl.NumberFormat` (locale, currency, fixed decimals) each frame.
- `font-variant-numeric: tabular-nums` so digits keep the same width; reserve the final width if needed.
- Animate related visuals (progress bars, sparklines) with the same easing and duration.
- Avoid: counting for more than 2s, starting before the number is visible, and counting huge numbers digit by digit.

## Acceptance criteria

1. Numbers count to their exact final value in 1–1.6s with ease-out, formatted correctly at every frame.
2. Digit width stays stable (tabular numbers).
3. Screen readers get only the final value; without JS the final value shows.
4. Works with mouse, touch and keyboard as described in the interaction contract.
5. Reduced-motion mode presents the same information without the movement described above.
6. Only `transform`, `opacity`, `filter`, colour and shadow animate; no layout thrash; smooth on a mid-range phone.
7. No console errors or leaks; listeners, observers, timers and animation frames are cleaned up.
8. Responsive at 375px, 768px and 1440px.

## Prompt terms

| English prompt line | 中文提示詞 |
| --- | --- |
| Make the stats Count Up from zero to their values over 1.4 seconds with ease-out when they scroll into view, using tabular numbers. | 數據做數字滾動（Count Up）：進入畫面時從零滾到目標值，1.4 秒，減速收尾，數字等寬。 |

## Copy-ready English prompt

```text
Add a count-up to these stats. Put the final value in the HTML (so it shows without JS) and in visually hidden text for screen readers; the animated number is aria-hidden. When a stat enters the viewport (once), run a requestAnimationFrame loop for 1.4s with ease-out-expo (1 - 2^(-10t)), formatting each frame with Intl.NumberFormat and keeping decimals, %, + and currency. Use font-variant-numeric: tabular-nums. Animate any related progress bar with the same timing. Under prefers-reduced-motion show the final values immediately.
```
