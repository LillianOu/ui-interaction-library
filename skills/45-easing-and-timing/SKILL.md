---
name: 45-easing-and-timing
description: Use when any animation in a page or app feels stiff, floaty, slow or random; sets the duration and easing curve for every move (enter, exit, move between, loop) so all other motion skills feel right. Easing & Timing (緩動與時長) rules with a cheat sheet and reduced-motion handling.
---
# 45 — 緩動與時長 / Easing & Timing

**Category:** 動效基礎 / Motion Foundations

## Effect

Easing is how speed changes during a move. Real objects don't start or stop instantly: things arriving slow down as they land, things leaving speed up as they go. Matching the curve and the duration to the size of the change is what separates motion that feels designed from motion that feels like a default. This is the base skill: every other motion skill in the library (46–60 and the older ones) uses these numbers.

## When to use

Use when setting up a motion system or tokens for a product, when an animation feels wrong and you can't say why, or alongside any other motion skill to pick its duration and curve. This skill is an interaction recipe, not an existing code component.

Part of the sixteen-effect motion set (45–60), inspired by the Douyin video 「非程序员AI开发必看教程：16种常见动画效果科普」 by 大锤和AI. Specs, prompts and demo are written for this library. Timing and easing follow 45 Easing & Timing.

## Timing and easing rules

| Size of change | Examples | Duration | Easing |
| --- | --- | --- | --- |
| Micro | Hover, press, toggle, checkbox | 100–200ms | ease-out |
| Small | Tooltip, dropdown, toast | 150–250ms | ease-out in, ease-in out |
| Medium | Panel, modal, card expand, reveal | 250–400ms | ease-out, or spring (46) |
| Large | Page transition, hero entrance | 400–700ms | ease-in-out, or spring (46) |
| Ambient loop | Beam, marquee, shimmer | 1.2–30s per cycle | linear, always pausable |

- **Enter = ease-out** (fast start, gentle landing). **Exit = ease-in** (gentle start, quick leave), about 25% shorter than the entrance. **Move between two places on screen = ease-in-out.** **Loops = linear.** Never linear for UI that moves from A to B.
- Default curves as tokens: `--ease-out: cubic-bezier(.2,.8,.2,1)`, `--ease-in: cubic-bezier(.4,0,1,1)`, `--ease-in-out: cubic-bezier(.65,0,.35,1)`, `--dur-micro: 160ms`, `--dur-small: 220ms`, `--dur-medium: 320ms`, `--dur-large: 520ms`.
- Distance matters: a move across a whole screen needs more time than one across a button. On phones, shorten durations by about 20% compared with desktop panels of the same role.
- One hero effect per screen. Motion must have a job: guide attention, show cause and effect, or show state. Remove motion that only decorates and delays.
## Interaction contract

- Input: applies to every state change, whatever triggered it.
- States: each animated property has an entering curve, an exiting curve and a duration taken from the table; hover-in and hover-out may differ (out faster).
- Cancellation and edge cases: an interrupted animation reverses from its current value with the opposite curve; it never jumps to the start. Rapid toggling must not queue animations.
- Accessibility: nothing important appears only after a long animation; content stays readable and clickable while it moves.
- Reduced motion: keep colour and opacity changes at 100–150ms; drop movement, scaling and parallax; loops stop.

## Implementation notes

- Define durations and curves once as CSS custom properties or design tokens and reuse them; don't write one-off `cubic-bezier` values per component.
- CSS transitions handle most UI; the Web Animations API (`element.animate`) for sequences; GSAP (32 GSAP Skills) or Motion / Framer Motion for timelines and springs.
- Check the curve by recording the screen and stepping frame by frame, or with browser DevTools' animation panel.
- Avoid: `ease` and `linear` defaults on UI moves, durations over 700ms for interface feedback, the same duration for tiny and large changes, and exits slower than entrances.

## Acceptance criteria

1. Every animation's duration and curve comes from the table or the shared tokens.
2. Entrances use ease-out, exits ease-in and shorter, moves ease-in-out, only loops are linear.
3. Interrupting any animation continues from its current value without a jump.
4. Reduced-motion mode presents the same information without the movement described above.
5. Only `transform`, `opacity`, `filter`, colour and shadow animate; no layout thrash; smooth on a mid-range phone.
6. No console errors or leaks; listeners, observers, timers and animation frames are cleaned up.
7. Responsive at 375px, 768px and 1440px.

## Prompt terms

| English prompt line | 中文提示詞 |
| --- | --- |
| Apply proper Easing everywhere: ease-out for things entering, ease-in for things leaving (about 25% faster), ease-in-out for things moving between places, linear only for loops. Micro-interactions 100–200ms, panels 250–400ms, page transitions 400–700ms. Put the curves and durations in shared tokens. | 全站統一緩動（Easing）：進場用減速（ease-out），離場用加速（ease-in）並快約 25%，位移用先加速後減速（ease-in-out），只有循環動畫用勻速。小動作 0.1–0.2 秒，面板 0.25–0.4 秒，頁面轉場 0.4–0.7 秒。曲線和時長做成共用變數。 |

## Copy-ready English prompt

```text
Set up a motion token system and apply it across this UI. Tokens: --ease-out cubic-bezier(.2,.8,.2,1), --ease-in cubic-bezier(.4,0,1,1), --ease-in-out cubic-bezier(.65,0,.35,1), --dur-micro 160ms, --dur-small 220ms, --dur-medium 320ms, --dur-large 520ms. Rules: entering = ease-out; exiting = ease-in and about 25% shorter; moving between two places = ease-in-out; only infinite loops are linear. Hover/press/toggle use micro, tooltips/dropdowns small, panels/modals medium, page and hero transitions large. Interrupted animations continue from their current value. Under prefers-reduced-motion keep short colour/opacity fades and remove movement, scale and parallax. Animate only transform, opacity, filter, colour and shadow.
```
