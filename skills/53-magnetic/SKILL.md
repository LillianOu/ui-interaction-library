---
name: 53-magnetic
description: Use when one primary call-to-action button should pull toward the cursor as it approaches and spring back when it leaves, on desktop. Magnetic (磁吸) button recipe with radius, pull strength, touch, keyboard and reduced-motion handling.
---
# 53 — 磁吸 / Magnetic

**Category:** 游標與懸停 / Cursor & Hover

## Effect

As the cursor comes near the button, the button drifts toward it as if magnetised, with its label moving a little further than the button itself. When the cursor moves away it springs back. It quietly draws attention to the one action that matters.

## When to use

Use for the single most important CTA on a landing page or hero, or a small set of icon buttons in a playful brand. Not for form buttons, dense toolbars or anything people click repeatedly. This skill is an interaction recipe, not an existing code component.

Part of the sixteen-effect motion set (45–60), inspired by the Douyin video 「非程序员AI开发必看教程：16种常见动画效果科普」 by 大锤和AI. Specs, prompts and demo are written for this library. Timing and easing follow 45 Easing & Timing.

## Interaction contract

- Input: fine pointer (mouse, trackpad) within a radius around the button. Touch and coarse pointers get the normal press state only.
- States: resting, attracted (follows pointer offset), pressed, returning.
- Cancellation and edge cases: pointer leaving the zone or the window returns the button; scroll and resize recalculate the centre; the click target always stays under the cursor when it is over the button.
- Accessibility: the button stays a real `<button>` or link with a visible focus style; keyboard focus doesn't move it.
- Reduced motion: no movement; standard hover colour change only.

## Implementation notes

- Listen to `pointermove` on a wrapper zone. Distance from the button's resting centre (subtract the current offset before measuring) < radius (~100px plus half the button width) → translate by offset × 0.3; label by an extra ~0.4 of that.
- Short linear transition while attracted (~120ms) and a spring transition (46) when releasing.
- Gate with `matchMedia('(hover: hover) and (pointer: fine)')`.
- Avoid: pull strength over ~0.5 (the button runs away from the click), magnetic effects on many buttons at once, and moving the hit area away from the pointer.

## Acceptance criteria

1. Within the radius the button drifts toward the pointer (about 30% of the offset) and springs back on leave.
2. Only fine pointers trigger it; touch and keyboard users get a normal button.
3. The button is always clickable where the cursor is.
4. Works with mouse, touch and keyboard as described in the interaction contract.
5. Reduced-motion mode presents the same information without the movement described above.
6. Only `transform`, `opacity`, `filter`, colour and shadow animate; no layout thrash; smooth on a mid-range phone.
7. No console errors or leaks; listeners, observers, timers and animation frames are cleaned up.
8. Responsive at 375px, 768px and 1440px.

## Prompt terms

| English prompt line | 中文提示詞 |
| --- | --- |
| Make the main call-to-action Magnetic: when the cursor comes within 100px the button drifts toward it, and springs back when the cursor leaves. Desktop only. | 主按鈕加磁吸效果（Magnetic）：游標靠近 100px 內時按鈕被吸過去，離開時彈回原位，只在桌面端。 |

## Copy-ready English prompt

```text
Make this primary button magnetic on desktop. Wrap it in a zone; on pointermove (fine pointers only, matchMedia('(hover: hover) and (pointer: fine)')), measure distance from the button's resting centre; within 100px plus half its width, translate the button by 30% of the offset and its label by a further 40% of that, with a 120ms linear transition. On leave, spring back (cubic-bezier(.34,1.56,.64,1), 500ms). Keep it a real button with a visible focus ring; focus doesn't move it. Under prefers-reduced-motion, or on touch, no movement.
```
