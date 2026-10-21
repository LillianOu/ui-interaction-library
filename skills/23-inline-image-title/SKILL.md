---
name: 23-inline-image-title
description: Use when a headline should carry a small rounded image inside the line of text that opens in place into a full-width photo. Inline Image Title (標題嵌小圖) recipe with keyboard, focus and reduced-motion handling.
---
# 23 — 標題嵌小圖 / Inline Image Title

**Category:** 排版互動 / Layout Relationships

## Effect

A large headline has a small rounded image sitting inside one of its lines, the same height as the letters, like a word made of picture. Tapping it grows the image in place into a full-width photo; the text above and below glides apart to make room instead of jumping. Tapping again shrinks it back into the line, and the words close around it.

## When to use

Use for editorial headers, story cards, travel journals, product launch pages and portfolio case-study intros, where the image adds mood and a second tap reveals the full picture without leaving the page. One inline image per headline is the strongest; two is the maximum. This skill is an interaction recipe, not an existing code component. For opening a card into a separate detail view, see 01 Shared Element Expansion.

## Interaction contract

- Input: click or tap on the image; Enter or Space when it is focused; Escape or a second activation collapses it.
- States: **inline** (image height = cap height or line height, width about 1.5–2.5× height, large radius), **expanding**, **expanded** (full content width, natural aspect ratio, optional caption), **collapsing**. Only one image open at a time if several exist.
- Interruption: a tap during the animation reverses from the current size, never restarts from the beginning.
- Edge cases: missing image keeps a tinted placeholder pill of the same size so line breaks do not change; headline reflow on resize keeps the image anchored to its word; expanded state stays correct after rotation.
- Accessibility: the image is a `<button>` with `aria-expanded` and an accessible name such as "Show photo: Lofoten at 7 am". The headline still reads as a sentence to screen readers (the image is not part of the heading text, or carries empty alt inside the heading and the name lives on the button). Focus stays on the button after toggling.
- Reduced motion: switch instantly between inline and expanded, or use a short crossfade; no height or position tweening.

## Implementation notes

- Layout: make the headline lines block-level spans so the image can sit on its own line during expansion. Size the inline pill with `height: 1cap` (or `0.8em` fallback) and `vertical-align: middle` or a flex row per line.
- Animation: use a FLIP approach. Measure the inline rect, switch the element to the expanded layout, measure again, then animate `transform` from the old rect to the new one while surrounding lines animate their `translateY` to their new positions. The View Transitions API (`document.startViewTransition` with a shared `view-transition-name`) is a clean option where supported. Framer Motion `layout` is the React shortcut.
- Use `object-fit: cover` and animate `border-radius` together with the scale so corners stay round (counter-scale the radius or use `clip-path: inset(... round r)`).
- Spring or ease-out-quint, roughly 450–600 ms; text should move with the same curve so it feels like one system.
- Load a small thumbnail for the inline state and swap to the full-resolution source before or during expansion with `srcset` / `decode()` so there is no blurry final frame.
- Avoid: animating `width`/`height` directly on large images, letting the page scroll jump when the content grows (keep the image's top edge visually stable or scroll it gently into view).

## Acceptance criteria

1. At rest the image matches the text height and the headline wraps the same with or without the image loaded.
2. Expanding and collapsing are smooth, reversible mid-way, and the surrounding text moves with the image, not after it.
3. Works by mouse, touch and keyboard; `aria-expanded` reflects the state; focus never jumps.
4. Reduced-motion mode toggles without tweening.
5. No layout shift outside the headline block; listeners and observers are cleaned up.
6. Responsive at 375px, 768px and 1440px.

## Copy-ready English prompt

```text
Create a reusable inline-image headline. A large multi-line headline contains one small rounded image placed inside a line of text, sized to the height of the letters, like a word made of picture. Make the image a button with aria-expanded and a descriptive accessible name. On click, tap, Enter or Space, expand it in place to full content width at its natural aspect ratio, while the lines above and below smoothly move apart to make room; a second activation or Escape collapses it back into the line and the text closes around it. Use a FLIP or View Transitions approach so only transform, opacity and clip-path animate, keep the corners rounded through the animation, and reverse from the current position if interrupted. Load a light thumbnail for the inline state and decode the full-size image before expansion. Keep line breaks stable with a placeholder if the image fails, keep page scroll stable, and keep the headline readable as plain text for screen readers. With prefers-reduced-motion, switch states instantly. Expose the headline text, image position, image sources, alt text and easing as props.
```
