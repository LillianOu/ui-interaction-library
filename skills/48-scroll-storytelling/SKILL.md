---
name: 48-scroll-storytelling
description: Use when a product or feature page should explain things one at a time as the reader scrolls, with the visual pinned in place while text steps pass by. Scroll Storytelling (滾動敘事) recipe with sticky layout, step detection, keyboard, mobile and reduced-motion handling.
---
# 48 — 滾動敘事 / Scroll Storytelling

**Category:** 滾動動效 / Scroll

## Effect

As the page scrolls, the product visual stays pinned while short feature steps scroll past beside it. The step in focus brightens and the visual changes to match it (a new screen, a number, a colour), so the page tells a story one point at a time.

## When to use

Use for product launch pages, feature tours, case studies and onboarding explainers with three to six points that share one visual. Not for long reading content or pages where people need to scan everything at once. This skill is an interaction recipe, not an existing code component.

Part of the sixteen-effect motion set (45–60), inspired by the Douyin video 「非程序员AI开发必看教程：16种常见动画效果科普」 by 大锤和AI. Specs, prompts and demo are written for this library. Timing and easing follow 45 Easing & Timing.

## Interaction contract

- Input: scroll by wheel, touch, keyboard (Page Down, Space, arrows) and scrollbar; steps can also be links that jump to their position.
- States: each step is upcoming, active or past; exactly one is active; the visual shows the active step's state.
- Cancellation and edge cases: fast flick scrolling skips through steps without the visual getting stuck between states; resizing recalculates; starting the page mid-way (anchor link, refresh) shows the correct step.
- Accessibility: every step's text is real, readable text in order; the visual change is decorative (`aria-hidden`) or described in the step text; nothing depends on scroll position to be readable.
- Mobile: below ~768px, pin the visual at the top (shorter) or drop the pin and put the visual inside each step.
- Reduced motion: no scrubbed animation; the visual swaps with a short fade when the active step changes.

## Implementation notes

- Layout: two columns; the visual column is `position: sticky; top: <header height>` with a height of about one viewport; each step is about 60–100vh tall.
- Detection: `IntersectionObserver` on the steps with a threshold around 0.6 (or a rootMargin band across the middle of the screen) marks the active step.
- Scrubbed variants (the visual animates continuously with scroll): GSAP ScrollTrigger with `pin` and `scrub` (32 Swift Swallow), or CSS `animation-timeline: view()`.
- Swap the visual's state with opacity/transform on pre-rendered layers rather than reloading images.
- Avoid: scroll-jacking (changing scroll speed or snapping hard), pins taller than the viewport, and more than about six steps.

## Acceptance criteria

1. The visual stays pinned while steps scroll, and exactly one step is active at a time.
2. The visual always matches the active step, including after a fast scroll or a page refresh mid-way.
3. Works with wheel, touch and keyboard scrolling; mobile layout is usable at 375px.
4. Works with mouse, touch and keyboard as described in the interaction contract.
5. Reduced-motion mode presents the same information without the movement described above.
6. Only `transform`, `opacity`, `filter`, colour and shadow animate; no layout thrash; smooth on a mid-range phone.
7. No console errors or leaks; listeners, observers, timers and animation frames are cleaned up.
8. Responsive at 375px, 768px and 1440px.

## Prompt terms

| English prompt line | 中文提示詞 |
| --- | --- |
| Build a Scroll Storytelling section: the product image stays pinned on the right while three feature steps scroll on the left; the active step highlights and the image changes to match. | 做一段滾動敘事（Scroll Storytelling）：右邊產品圖固定不動，左邊三個賣點依次滾過，當前賣點高亮，圖片跟著切換。 |

## Copy-ready English prompt

```text
Build a Scroll Storytelling section. Two columns: steps on the left, each about 80vh tall with a heading and one line; on the right a visual with position: sticky, top under the header, one viewport tall. An IntersectionObserver (threshold 0.6) marks the active step: it goes to full opacity with an accent left border, others sit at 35% opacity, and the visual crossfades (300ms ease-out) to that step's state. No scroll-jacking. Below 768px pin a shorter visual at the top or move it into each step. The visual is aria-hidden or described by the step text. Under prefers-reduced-motion use instant swaps. Refreshing mid-page shows the right step.
```
