---
name: 52-tilt
description: Use when one physical-looking object (a membership card, product shot, ticket, badge) should tilt in 3D toward the cursor with a moving glare. Tilt (3D 傾斜) recipe with perspective, glare, touch drag, keyboard and reduced-motion handling.
---
# 52 — 3D 傾斜 / Tilt

**Category:** 游標與懸停 / Cursor & Hover

## Effect

The card rotates in 3D toward the cursor, as if you were holding it and turning it in the light; a glare slides across the surface as it moves. When the cursor leaves it springs back flat.

## When to use

Use for a single hero object: a membership or gift card, a product, a ticket, a collectible. Not for every card in a grid (too busy) or anything with text people need to read while it moves. This skill is an interaction recipe, not an existing code component.

Part of the sixteen-effect motion set (45–60), inspired by the Douyin video 「非程序员AI开发必看教程：16种常见动画效果科普」 by 大锤和AI. Specs, prompts and demo are written for this library. Timing and easing follow 45 Easing & Timing.

## Interaction contract

- Input: pointer move over the card on desktop; on touch, drag over the card (with `touch-action: none` on the card only); keyboard: arrow keys nudge the tilt, Escape or blur resets.
- States: resting (flat), tilting, returning (spring back).
- Cancellation and edge cases: pointer leave, `pointercancel` and blur reset it; angles are clamped; resize re-measures.
- Accessibility: the card has an accessible name (`role="img"` with `aria-label`, or real text); tilt is decorative.
- Reduced motion: the card stays flat; a static glare is fine.

## Implementation notes

- Parent `perspective: 800px`; card `transform: rotateX(var(--rx)) rotateY(var(--ry))` with `transform-style: preserve-3d`.
- From pointer position normalised to [-0.5, 0.5]: `rx = -py × 2 × max`, `ry = px × 2 × max`, max 8–12°. Update in `requestAnimationFrame`.
- Glare: `::after` radial gradient positioned at the pointer, `mix-blend-mode: soft-light` or `overlay`.
- Short linear transition while moving (~80ms); spring transition (46) on reset.
- Avoid: angles over ~15°, tilting large layout areas, and blocking page scroll on touch outside the card.

## Acceptance criteria

1. The card tilts toward the pointer up to about 10°, with a glare that follows.
2. It springs back flat on leave, cancel or blur.
3. Touch drag and arrow keys also tilt it; page scroll is unaffected outside the card.
4. Works with mouse, touch and keyboard as described in the interaction contract.
5. Reduced-motion mode presents the same information without the movement described above.
6. Only `transform`, `opacity`, `filter`, colour and shadow animate; no layout thrash; smooth on a mid-range phone.
7. No console errors or leaks; listeners, observers, timers and animation frames are cleaned up.
8. Responsive at 375px, 768px and 1440px.

## Prompt terms

| English prompt line | 中文提示詞 |
| --- | --- |
| Make the membership card Tilt in 3D toward the cursor, max 10 degrees, with a moving glare; it springs back flat when the cursor leaves. | 會員卡做 3D 傾斜（Tilt）：跟著游標方向傾斜，最多 10 度，帶反光；游標離開時彈回平放。 |

## Copy-ready English prompt

```text
Add a 3D tilt to this card. Wrap it in a parent with perspective: 800px. On pointermove, normalise the pointer to [-0.5, 0.5] across the card and set rotateX(-py × 20deg) rotateY(px × 20deg) (max 10°) in requestAnimationFrame, with a ::after radial-gradient glare positioned at the pointer (mix-blend-mode soft-light). Use a 80ms linear transition while moving and a spring (cubic-bezier(.34,1.56,.64,1), 500ms) to return flat on pointerleave, pointercancel or blur. Touch: drag tilts it (touch-action: none on the card only). Keyboard: arrow keys nudge, Escape resets. Give the card an accessible name. Under prefers-reduced-motion keep it flat.
```
