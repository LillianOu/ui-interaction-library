---
name: 43-card-to-hero-carousel
description: Use when a full-bleed hero should cycle through places, products or projects shown as a row of cards, where tapping a card grows it into the new hero background. Card-to-Hero Carousel (卡片展開輪播) recipe covering pointer, touch, keyboard, accessibility and reduced motion.
---
# 43 — 卡片展開輪播 / Card-to-Hero Carousel

**Category:** 導覽與視圖 / Navigation & Views

## Effect

A full-bleed hero shows one item large, with headline copy on the left and the next items queued as portrait cards on the right. Tapping a card makes it grow from its exact spot until it fills the hero and becomes the new background. The headline swaps with a short stagger, the remaining cards slide left to close the gap, the old hero rejoins the queue at the end, and a progress line plus a big counter update.

It is often described as cards "opening like an envelope", but nothing folds or flips: it is one image expanding from card to full screen (a shared-element transition inside a carousel).

## When to use

Use for travel and destination pages, portfolio and case-study heroes, product collections, event line-ups and campaign landing pages: anywhere the visuals are strong and there are roughly 4–8 items worth browsing. This skill is an interaction recipe with a working reference demo, not a packaged component.

Do not use it for text-heavy content, for more than about 10 items (the queue becomes a scroller nobody uses), or for anything users must compare side by side. If a card should open a separate detail page rather than replace the hero, use **01 Shared Element Expansion** instead.

## Anatomy

| Part | Role |
| --- | --- |
| Background layer | The current item's image, full bleed, `object-fit: cover` behaviour |
| Shade | Gradient over the background so white copy stays readable on any image |
| Copy block | Small rule, region/eyebrow, big title, 2–3 line description, one CTA |
| Queue (rail) | Portrait cards for the next items in order, starting right of centre and running off the edge |
| Controls | Previous / next buttons, progress line, large slide number |
| Grow layer | A temporary copy of the clicked card's image that animates to full size, then is removed |

## Interaction contract

- **Input:** click or tap a card; previous / next buttons; ← / → keys while focus is inside the carousel; horizontal swipe on touch (threshold about 50px, horizontal movement clearly larger than vertical). Swipes must not also fire a click.
- **Sequence (about 1.2s total):**
  1. Copy fades up and out (about 220ms, slight stagger).
  2. The grow layer starts at the card's exact rectangle and radius and animates `left / top / width / height / border-radius` to cover the hero (about 750ms, strong ease-in-out such as `cubic-bezier(.7,0,.2,1)`). The real card is hidden while the layer stands in for it. The queue stays above the growing image, as in the reference.
  3. Commit: swap the background to the new item, remove the layer, update copy, progress and counter.
  4. Copy fades in from below with a 60ms stagger; queued cards slide left into their new positions using FLIP; the previous hero enters at the end of the queue from the right.
- **Which transition runs:** grow only when the target card is visible on screen. Next = first card, so it grows. Previous is usually the last card and off screen, so it crossfades. Reduced motion always crossfades.
- **Interruption:** never stack two grows. While animating, store only the latest request and run it when the current one finishes. Relative controls (next, previous, arrow keys, swipe) count from where the carousel is heading, so three quick "next" taps move three slides, not one.
- **Edge cases:** wrap around at both ends; one item = no queue and no controls; two items = next and previous lead to the same slide; resize mid-animation is allowed to finish and the next state is laid out fresh; missing image falls back to a solid brand colour, never a broken icon; images not yet loaded should be preloaded for the next one or two items.
- **Accessibility:** the carousel is a `region` with `aria-roledescription="carousel"` and a label. Cards are real `<button>`s with labels like "Show Iron Peaks, Granite Range". The title is a real heading. A visually hidden `aria-live="polite"` region announces "Iron Peaks, Granite Range. Slide 3 of 6." after each change; do not make the whole copy block live. If focus was on the clicked card, move it to the new first card so keyboard users keep moving forward. Decorative images get `aria-hidden` or empty `alt`; the image that carries meaning gets real `alt` text. Do not autoplay by default; if autoplay is required, pause on hover, focus and `visibilitychange`, and provide a visible pause button (WCAG 2.2.2).
- **Reduced motion:** no growing, no sliding queue, no staggered copy. Crossfade the new background and copy in about 200ms and reorder the queue instantly. All information stays the same.

## Implementation notes

- **Vanilla first.** The reference demo uses the Web Animations API only: one `animate()` on the grow layer, small WAAPI fades for the copy, and FLIP for the queue (record each card's `left`, reorder the DOM, animate `translateX(old − new)` to `none`). No library needed. Use GSAP (see **32 Swift Swallow**) only if you add a longer timeline, such as a parallax drift on the background.
- **Keep one element per item** and reorder it with `appendChild`; never rebuild the queue's HTML, or FLIP has nothing to track and focus is lost.
- **Why animate `width/height` and not `scale`:** the card is portrait and the hero is landscape, so scaling would stretch the image. Animating the box with the image set to cover lets the crop widen naturally, which is what makes the effect feel like the photo "opens up". It is one absolutely positioned element inside a contained stage, so the layout cost is small. If profiling shows jank on low-end phones, switch to animating `clip-path: inset(...) round 14px` on a full-size layer instead.
- **Match the first frame:** the grow layer must use the same image, crop rule and radius as the card, positioned from `getBoundingClientRect()` relative to the stage, or users see a jump at the start.
- **Layers (z-index):** background 0 → grow layer 1 → shade 2 → copy, queue and controls 3.
- **Mobile (≤720px):** copy moves to the top, description clamps to three lines, cards shrink to about 118px wide, the shade turns into a top-and-bottom vertical gradient, controls run full width at the bottom.
- **Images:** use original or properly licensed photography. Serve sized `srcset` images; the hero needs about 2000px wide, cards about 400px. Preload the next item's hero image.
- **Avoid:** a carousel as the only way to reach important content; tiny text over busy images without a shade; animating `top/left` on many elements at once; hijacking vertical scroll; autoplay that cannot be paused.

## Adjustable parameters

| Parameter | Default | Notes |
| --- | --- | --- |
| Grow duration | 760ms | 600–900ms feels premium; under 500ms looks like a glitch |
| Grow easing | `cubic-bezier(.7,0,.2,1)` | Slow start, fast middle, soft landing |
| Copy out / in | 220ms / 440ms, 60ms stagger | |
| Queue slide | 560ms | Starts with the copy-in |
| Card size | `clamp(150px, 13vw, 190px)`, 2:3 | 118px on mobile |
| Accent | `#E8B04B` progress line | Swap for the brand colour |

## Acceptance criteria

1. Clicking any visible card grows it from its exact position and radius into the full hero with no first-frame jump.
2. After every transition the queue is in correct wrap-around order, the old hero is last, and no grow layers are left in the DOM.
3. Next grows from the first card; previous crossfades when its card is off screen; three quick taps move three slides.
4. Works with mouse, touch (tap and swipe, no double-firing) and keyboard (Tab + Enter, ← →), with visible focus on cards and buttons.
5. Screen readers hear one announcement per change, and cards have descriptive labels.
6. Reduced motion crossfades in about 200ms with the same content and order.
7. No horizontal page scroll and readable copy at 375px, 768px and 1440px.
8. No console errors; listeners are removed and running animations cancelled if the component unmounts.

## Live demo

`demo/43-card-to-hero-carousel.html` is a complete, dependency-free reference implementation. The CSS and the single script in that page are the whole interaction: copy them, then replace the generated SVG scenes with real images.

## Copy-ready English prompt

```text
Build a reusable Card-to-Hero Carousel. A full-bleed hero shows the current item (background image, gradient shade, eyebrow, large title, short description, one CTA) and the next items as a row of 2:3 portrait cards starting right of centre. When a visible card is clicked, create a temporary layer with the same image, crop and border radius at the card's exact rectangle, hide the card, and animate the layer's left/top/width/height/border-radius to fill the hero in about 750ms with cubic-bezier(.7,0,.2,1). Meanwhile fade the copy out. Then swap the background to the new item, remove the layer, stagger the new copy in, and slide the remaining cards left using FLIP while the previous hero rejoins the end of the queue. Keep one DOM element per item and reorder it rather than rebuilding. Include previous/next buttons (next grows from the first card; previous crossfades when its card is off screen), a progress line and a large slide number. Support click, tap, horizontal swipe without double-firing, and ← → keys. While animating, queue only the latest request, and count relative moves from the pending target. Cards are buttons with descriptive labels, a polite live region announces "Title, region. Slide X of N.", and focus moves to the new first card if the clicked card had focus. No autoplay by default. With prefers-reduced-motion, crossfade in about 200ms instead. Make it work at 375px (copy on top, smaller cards) through 1440px, use Web Animations API with no dependencies, and clean up animations on unmount.
```
