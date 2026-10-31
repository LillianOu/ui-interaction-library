---
name: 59-marquee
description: Use when a strip of customer logos, testimonials or tags should scroll endlessly across the page, with rows in opposite directions, edge fades and a pause. Marquee (跑馬燈) recipe with seamless looping, pause controls, screen readers and reduced-motion handling.
---
# 59 — 跑馬燈 / Marquee

**Category:** 氛圍與吸睛 / Ambient & Attention

## Effect

Rows of logos or quotes slide sideways in an endless loop, each row in the opposite direction, fading out at the edges. It shows a lot of social proof in little space and keeps the section gently alive.

## When to use

Use for 'trusted by' logo walls, testimonial strips, tag clouds and partner lists. Not for content people must read carefully or click precisely while it moves, and not more than one marquee section per page. This skill is an interaction recipe, not an existing code component.

Part of the sixteen-effect motion set (45–60), inspired by the Douyin video 「非程序员AI开发必看教程：16种常见动画效果科普」 by 大锤和AI. Specs, prompts and demo are written for this library. Timing and easing follow 45 Easing & Timing.

## Interaction contract

- Input: none to run; hover, keyboard focus inside it, and a pause button stop it. On touch, tapping the pause button stops it.
- States: running, paused, static (reduced motion).
- Cancellation and edge cases: the loop is seamless at any viewport width (the duplicated set must be wider than the screen); pauses off screen; items stay clickable when paused.
- Accessibility: the list is read once: the duplicate copy is `aria-hidden` and its links get `tabindex="-1"`; it runs longer than 5s so a visible pause control is required (WCAG 2.2.2).
- Reduced motion: rows stop and become horizontally scrollable.

## Implementation notes

- Track = items + a duplicate of the items, `width: max-content`; `animation: marquee 20–40s linear infinite` with `to { transform: translateX(calc(-50% - gap/2)) }`.
- Alternate rows with `animation-direction: reverse` and different durations.
- Edge fade with `mask-image: linear-gradient(90deg, transparent, #000 12%, #000 88%, transparent)`.
- Pause with `animation-play-state: paused` on `:hover`, `:focus-within` and a `.paused` class toggled by the button.
- Avoid: JS scroll loops when CSS works, speeds so fast that text can't be read, and loops that jump at the reset point.

## Acceptance criteria

1. Rows loop seamlessly with no visible jump, alternating direction, with faded edges.
2. Hover, focus and a visible button pause it.
3. Screen readers and keyboard users meet each item only once.
4. Works with mouse, touch and keyboard as described in the interaction contract.
5. Reduced-motion mode presents the same information without the movement described above.
6. Only `transform`, `opacity`, `filter`, colour and shadow animate; no layout thrash; smooth on a mid-range phone.
7. No console errors or leaks; listeners, observers, timers and animation frames are cleaned up.
8. Responsive at 375px, 768px and 1440px.

## Prompt terms

| English prompt line | 中文提示詞 |
| --- | --- |
| Add a Marquee of customer logos and quotes: two rows scrolling endlessly in opposite directions, fading at the edges, pausing on hover, with a pause button. | 加一條跑馬燈（Marquee）：客戶標誌和評價兩排反向無限循環滾動，兩端漸隱，懸停暫停，並提供暫停按鈕。 |

## Copy-ready English prompt

```text
Build a marquee section with two rows (logos, then testimonials). Each row's track holds the items followed by an aria-hidden duplicate (links in the duplicate get tabindex=-1), width: max-content, animated translateX(0 → calc(-50% - gap/2)) linear infinite, 26s for row one and 34s reversed for row two. Fade the edges with mask-image linear-gradient(90deg, transparent, #000 12%, #000 88%, transparent). Pause on hover, on focus-within and with a visible Pause/Play button; pause when off screen. Under prefers-reduced-motion stop the animation and make each row horizontally scrollable.
```
