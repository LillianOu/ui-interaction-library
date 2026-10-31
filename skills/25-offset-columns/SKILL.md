---
name: 25-offset-columns
description: Use when a two-column image gallery should scroll its columns at different speeds so they stay staggered, then land with their bottom edges aligned. Offset Columns (兩列錯速滾動) parallax recipe with reduced-motion and touch-safe handling.
---
# 25 — 兩列錯速滾動 / Offset Columns

**Category:** 網格與面板 / Grids & Panels

## Effect

A two-column photo stream where the columns travel at different speeds while the page scrolls: one column moves about 1.5× faster than the other, so the images keep sliding past each other and never line up into a rigid grid. When the reader reaches the end of the gallery, both columns arrive together and their bottom edges line up neatly.

## When to use

Use for photo galleries, mood boards, portfolio project feeds, product lookbooks and travel albums with mixed image ratios. The motion adds depth without any extra control. Not for content the user must compare row by row, such as pricing or data tables. This skill is an interaction recipe, not an existing code component.

## Interaction contract

- Input: normal page or container scroll from wheel, trackpad, touch, keyboard and scrollbar. No custom gestures; the user's scroll speed is never changed.
- Behaviour: within the gallery's scroll range, the faster column covers its full height while the slower column covers a shorter distance, so they finish at the same moment with aligned bottom edges. Before the gallery enters and after it leaves, both columns are still.
- States: **before**, **in range** (offset proportional to progress), **end** (bottoms aligned), plus reverse on scroll up.
- Edge cases: columns of unequal natural height (the speed ratio is derived from the heights, not hard-coded, so alignment still works), images loading late and changing heights (recalculate after load and on resize), very few images, one-column layout on narrow screens (disable the effect).
- Accessibility: the DOM order of images is the reading order (alternate between columns or list left column then right, and say which). Every image has alt text or is marked decorative. Focusable items inside images (links, buttons) stay visible and reachable when focused; scroll them into view normally.
- Reduced motion: both columns scroll at the same native speed with the bottoms aligned by a static offset or padding.

## Implementation notes

- Structure: a sticky or pinned wrapper whose height equals the taller column; the two columns are inside, and each is translated on the Y axis by `progress × (columnHeight − viewportHeight)`. Speed ratio = tallColumnTravel / shortColumnTravel, which naturally lands near 1.5 when one column holds more or taller images.
- An alternative without pinning: let the slow column be the normal flow and translate the fast column upward by `progress × extra`, where `extra` is the height difference; bottoms meet at the end of the range.
- Bind progress with CSS scroll-driven animations (`animation-timeline: view()`) where available, or GSAP ScrollTrigger with `scrub`, or an `IntersectionObserver` + `requestAnimationFrame` fallback. Animate only `transform`.
- Number badges or captions on the images help people keep their place while columns slide.
- Add `will-change: transform` only while the gallery is in view.
- Avoid: smooth-scroll libraries that hijack the native scroll, recomputing layout on every scroll event, translating so far that images detach visibly from the gallery edges.

## Acceptance criteria

1. While scrolling through the gallery, the two columns move at clearly different speeds (default ratio about 1.5:1) and stay staggered.
2. At the end of the gallery both column bottoms align exactly, at any viewport width where the effect is on.
3. Scrolling back up reverses smoothly with no jumps; late-loading images do not break alignment.
4. Native scrolling, keyboard scrolling and focus visibility are unaffected.
5. Reduced-motion and single-column modes show a normal, aligned gallery.
6. Smooth on a mid-range phone; observers and triggers are cleaned up. Responsive at 375px, 768px and 1440px.

## Copy-ready English prompt

```text
Create a reusable two-column offset gallery. Place images of mixed aspect ratios in two columns. While the gallery is scrolling through the viewport, move the columns at different speeds so the faster one travels about 1.5 times as far as the slower one and the images stay staggered. Derive the speed ratio from the two columns' real heights so that, at the end of the gallery, both columns finish together with their bottom edges exactly aligned. Before and after the gallery range, both columns are still. Use the native page scroll without hijacking it, bind progress with CSS scroll-driven animations or a GSAP ScrollTrigger scrub fallback, animate only transform, and recalculate after images load and on resize. Below 600px, collapse to one column and disable the effect. Keep a logical DOM reading order, alt text and visible focus for any links. With prefers-reduced-motion, scroll both columns at normal speed with bottoms aligned statically. Add small number badges on images and expose images, speed ratio and breakpoint as props.
```
