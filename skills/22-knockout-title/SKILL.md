---
name: 22-knockout-title
description: Use when a hero or cover needs a huge headline that a photo shows through, and scrolling should zoom the type until the photo fills the screen. Knockout Title (鏤空大標題) scroll-linked recipe with reduced-motion and readability fallbacks.
---
# 22 — 鏤空大標題 / Knockout Title

**Category:** 排版互動 / Layout Relationships

## Effect

A very large headline acts as a window: the photo is only visible inside the letterforms, while the rest of the panel is a flat or softly tinted surface. As the reader scrolls down, the letters scale up from the centre of the viewport until the counters and strokes grow past the edges and the photo fills the whole screen. Scrolling back up reverses the same path exactly, so the title closes back around the image.

## When to use

Use for the opening of a destination guide, editorial story, product launch or portfolio case study, where one strong image and one short word (a place, a product, a name) carry the page. Works best with 1–8 characters of a heavy display face. Not for long headlines, body copy or anything the reader must read quickly. This skill is an interaction recipe, not an existing code component.

## Interaction contract

- Input: vertical scroll (wheel, trackpad, touch, keyboard Page Down / Space / arrows, scrollbar drag). No click is required.
- States: **resting** (full word visible, photo inside the glyphs), **zooming** (scale tied to scroll progress), **revealed** (photo full-bleed, title gone), **reversing** (same curve backwards). Progress is a pure function of scroll position; never a one-shot animation that can drift out of sync.
- Pinning: the hero stays pinned for a set scroll distance (for example 150–250% of viewport height), then releases so the page continues normally.
- Edge cases: images that fail to load show a solid fill inside the glyphs, not transparent holes; very short viewports reduce the pin distance; resize and orientation changes recompute the scale target; a deep link or reload mid-page lands in the correct state.
- Accessibility: the visible headline is real text (or has an equivalent heading with the same words). Clipped text must not be the only copy of the title; decorative layers get `aria-hidden="true"`. The photo needs alt text if it carries meaning, or empty alt if purely decorative.
- Reduced motion: with `prefers-reduced-motion: reduce`, skip the pin and zoom. Show the knockout title statically, followed by the full photo as a normal block, or crossfade between the two at one threshold.

## Implementation notes

- **Knockout technique (pick one):**
  - CSS: `background-clip: text` with `color: transparent` and the photo as the text's background. Simple, keeps real text, good for a single line.
  - SVG mask: `<mask>` containing `<text>` in white over black, applied to an `<image>`. Better control of multi-line layout and scaling around a precise origin.
  - Blend mode: white text with `mix-blend-mode: multiply` over the image on a light panel. Cheapest, but colour accuracy depends on the panel.
- **Zoom:** scale the mask or text layer with `transform: scale()` from `transform-origin` at the visual centre of the word (often a counter, such as the hole of an O or the gap between letters, so the zoom "flies through" the type). Use an ease-in curve so the start feels calm and the end rushes open. Target scale is usually 20–60× and should be computed from viewport size, not hard-coded.
- **Scroll binding:** prefer CSS scroll-driven animations (`animation-timeline: view()` or `scroll()`) where supported, with GSAP ScrollTrigger (`scrub: true`, `pin: true`) or an `IntersectionObserver` + `requestAnimationFrame` loop as the fallback. Animate only `transform` and `opacity`.
- Keep the photo still or give it a small counter-scale for depth; do not animate its `background-position` every frame.
- Hide the surrounding labels (kicker, page counter) with an opacity fade in the first 20% of progress so they do not get magnified.
- Avoid: rasterising the title into an image, layout-thrashing reads inside scroll handlers, scroll-jacking that changes the user's scroll speed.

## Acceptance criteria

1. The photo is visible only inside the glyphs at rest, and fills the viewport at the end of the pinned range with no gaps or seams.
2. Scrolling forward and backward produces the same frames at the same positions; no jumps when changing direction.
3. Real, selectable or screen-reader-available heading text exists for the title.
4. Reduced-motion mode presents the title and the photo without zoom or pinning.
5. 60fps on a mid-range phone; only compositor properties animate; listeners and ScrollTriggers are cleaned up on unmount.
6. Responsive at 375px, 768px and 1440px, including portrait phones where the word must wrap or shrink.

## Copy-ready English prompt

```text
Create a reusable knockout hero title. A short, very heavy headline (for example a city name) acts as a cut-out window: a photo is visible only inside the letterforms, on a calm tinted panel with a small kicker label and page counter. Pin the hero while the user scrolls a set distance (about 2 viewport heights). Over that range, scale the title from a transform-origin at the visual centre of the word, with an ease-in curve, until the photo fills the whole viewport; then release the pin. Scrolling back up must reverse the exact same path, because progress is derived from scroll position, not a timed animation. Fade the kicker and counter out early so they are not magnified. Build the knockout with SVG mask or background-clip: text, keep a real heading with the same words for accessibility, compute the target scale from the viewport size, and recompute on resize and orientation change. Use CSS scroll-driven animations with a GSAP ScrollTrigger or requestAnimationFrame fallback, animating only transform and opacity. With prefers-reduced-motion, show the knockout title and then the full photo as static blocks. Provide a solid fallback fill if the image fails to load, and expose the word, image, pin distance and easing as props.
```
