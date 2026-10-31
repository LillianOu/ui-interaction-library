---
name: 14-cursor-driven-hero
description: Use when a landing page or portfolio hero should feel alive under the cursor without hiding its message. Layered parallax depth plus a soft spotlight that reveals a second layer, with touch, keyboard and reduced-motion fallbacks.
---
# 14 — 游標驅動的動態主視覺 / Cursor-driven Animated Hero

**Category:** 游標與懸停 / Cursor & Hover

## Effect

The hero is built from a few depth layers: background shapes, a headline and a foreground object. As the cursor moves, the layers shift by different amounts so the scene gains depth, and a soft spotlight follows the pointer, revealing a hidden second layer (a colour version of the headline, a sketch under a render, a keyword). The headline and call to action stay readable and still enough to click at all times.

## When to use

Use for the first screen of a portfolio, product launch or campaign page, where one strong idea should invite exploration. Do not use on pages people visit to get a task done (dashboards, checkout), and do not put essential information only in the revealed layer. This skill is an interaction recipe, not an existing code component. For a free-flowing light trail instead of a structured hero, use 09 Cursor-driven Luminous Flow.

## Interaction contract

- Input: `pointermove` over the hero section; position normalised to −1…1 from the centre. `pointerleave` eases everything back to rest.
- Depth: each layer has a depth value (for example 0.2 background, 0.5 headline, 1 foreground) and moves by `depth × maxShift` (about 8–24px). Use opposite directions for background and foreground to exaggerate depth. Optional tilt up to 4–6°.
- Smoothing: follow the pointer with damping (lerp about 0.08–0.15 per frame) so movement feels weighty, not jittery.
- Spotlight: a radial mask (radius about 120–220px, soft edge) centred on the pointer reveals the second layer. The revealed layer must be decorative or a duplicate of visible content.
- Touch: never require hover. On touch devices, run a slow ambient drift of the spotlight and layers, and let a drag move the spotlight while the finger is down; release returns to the drift.
- Keyboard: the hero is not a control. CTAs stay ordinary links or buttons in normal tab order. When a CTA has focus, centre the spotlight on it so keyboard users see the same reveal.
- Edge cases: pause the animation loop when the hero is off screen (`IntersectionObserver`) or the tab is hidden; recompute bounds on resize and scroll; never trap scroll.
- Accessibility: the moving layers are `aria-hidden` decoration; the real headline is plain text, not only an image or canvas. Contrast of headline and CTA must pass in every spotlight position.
- Reduced motion: no parallax, tilt or drift. Show a static composition with the spotlight fixed in a meaningful position, or the second layer revealed in a fixed area.

## Implementation notes

- CSS custom properties are enough: write `--mx`, `--my` (smoothed −1…1) and `--sx`, `--sy` (spotlight px) on the hero from one `requestAnimationFrame` loop, and let CSS do `transform: translate3d(calc(var(--mx) * var(--d) * 20px), …)` and `mask-image: radial-gradient(circle at var(--sx) var(--sy), #000 0, transparent 180px)`.
- Animate only `transform`, `opacity` and the mask position; never layout properties.
- In React, keep the loop in one effect with refs, write to the element's style directly (no state per frame), and cancel the frame and listeners on unmount.
- Use original or licensed images. Large foreground images should be compressed and sized for the hero.

## Acceptance criteria

1. Works with mouse; touch gets ambient drift plus drag; keyboard focus on a CTA moves the spotlight.
2. Headline and CTAs remain readable and clickable in every pointer position.
3. Reduced-motion mode shows a static composition with the same information.
4. The loop pauses off screen and in hidden tabs; no console errors or leaks after unmount.
5. Responsive at 375px, 768px and 1440px; holds 60fps on a mid-range phone.

## Copy-ready English prompt

```text
Create a reusable cursor-driven hero section. Build it from three depth layers (background shapes, headline, foreground object) that shift by different amounts with damped pointer movement, plus a soft radial spotlight that follows the pointer and reveals a decorative second layer. Keep the headline as real text and the CTAs as normal links in tab order. On touch, use a slow ambient drift and let dragging move the spotlight. When a CTA is focused by keyboard, centre the spotlight on it. Pause when off screen or the tab is hidden. With prefers-reduced-motion, show a static composition with no parallax. Drive everything with CSS custom properties from one requestAnimationFrame loop, animate only transform, opacity and mask position, and expose maxShift, damping, spotlight radius and layer depths as settings.
```
