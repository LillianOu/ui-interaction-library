---
name: 46-spring
description: Use when a like, toggle, slider, drag release or playful element should feel physical, with a slight overshoot that settles, instead of a plain ease-out. Spring (彈性) motion recipe with physics values, CSS linear() easing, touch, keyboard and reduced-motion handling.
---
# 46 — 彈性 / Spring

**Category:** 動效基礎 / Motion Foundations

## Effect

The element moves past its target a little and settles back, like a real object on a spring. It reads as lively and responsive, and because a spring keeps its velocity, a move that gets interrupted carries on naturally instead of restarting.

## When to use

Use for likes and reactions, toggles, slider and drag handles on release, bottom sheets snapping, and playful brand moments. Don't use it on dense data UI, form validation or anything serious (payments, errors): there, plain ease-out from 45 is calmer. This skill is an interaction recipe, not an existing code component.

Part of the sixteen-effect motion set (45–60), inspired by the Douyin video 「非程序员AI开发必看教程：16种常见动画效果科普」 by 大锤和AI. Specs, prompts and demo are written for this library. Timing and easing follow 45 Easing & Timing.

## Interaction contract

- Input: triggered by any state change (click, tap, key press, drag release); on drag release, the spring starts with the pointer's release velocity.
- States: at rest, moving, settling; a second trigger mid-move retargets the spring from its current position and velocity.
- Cancellation and edge cases: rapid clicks never stack overshoots; very short distances should not visibly wobble (raise damping or skip the spring).
- Accessibility: the state change (liked, on, value) is reflected in ARIA (`aria-pressed`, `aria-checked`, `aria-valuenow`) immediately, not after the spring settles.
- Reduced motion: no overshoot; instant change or a 120ms opacity/colour fade.

## Implementation notes

- Good default physics: stiffness ~170, damping ~14–26, mass 1. Lower damping = more bounce. Keep overshoot under ~10% of the distance for UI.
- CSS: generate a `linear()` easing from a spring simulation (sample 40–60 points) and use it as the transition timing function; fall back to `cubic-bezier(.34,1.56,.64,1)` where `linear()` is unsupported.
- JS: Motion / Framer Motion `type: "spring"`, react-spring, or GSAP `elastic`/custom ease; Web Animations API with the generated `linear()` string.
- Spring only `transform` (translate, scale, rotate). Springing `width` or `height` causes layout jank.
- Avoid: bounce on every element, long wobbles over ~900ms, and springs on exits (exits should leave quickly with ease-in).

## Acceptance criteria

1. Overshoot is visible but small (under ~10%) and settles within ~0.9s.
2. Retriggering mid-move continues from the current position without a jump.
3. ARIA state updates immediately on trigger.
4. Reduced-motion mode presents the same information without the movement described above.
5. Only `transform`, `opacity`, `filter`, colour and shadow animate; no layout thrash; smooth on a mid-range phone.
6. No console errors or leaks; listeners, observers, timers and animation frames are cleaned up.
7. Responsive at 375px, 768px and 1440px.

## Prompt terms

| English prompt line | 中文提示詞 |
| --- | --- |
| Use Spring motion for the like button and the slider handle: a small overshoot that settles, instead of a plain ease-out. Stiffness about 170, damping about 14. | 點讚按鈕和滑桿用彈性動效（Spring）：輕微超出再回彈定位，不要普通的減速。剛度約 170，阻尼約 14。 |

## Copy-ready English prompt

```text
Add spring motion to this UI's likes, toggles and draggable handles. Simulate a damped spring (stiffness 170, damping 14, mass 1), sample it into a CSS linear() easing (about 48 points) and use it as the transition timing function for transform only, falling back to cubic-bezier(.34,1.56,.64,1). The like icon pops from scale .4 to 1 on activate; toggles and handles overshoot slightly and settle in under 0.9s. Retriggering mid-move continues from the current value. Update aria-pressed / aria-checked / aria-valuenow immediately. Under prefers-reduced-motion, swap state instantly or with a 120ms fade. Clean up any animation frames.
```
