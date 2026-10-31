---
name: 58-border-beam
description: Use when one recommended plan, new feature or primary card should stand out with a short bright arc of light travelling around its border. Border Beam (邊緣流光) recipe with conic gradient, masking, pause control and reduced-motion handling.
---
# 58 — 邊緣流光 / Border Beam

**Category:** 氛圍與吸睛 / Ambient & Attention

## Effect

A short, bright arc of light travels continuously around the card's border, like a beam circling it. Among similar cards, the eye goes straight to the one with the beam.

## When to use

Use to mark the recommended pricing plan, a new feature, an AI input box or a primary card, usually on a dark background. Only one element per screen. Not on many cards, on light backgrounds where it barely shows, or on anything that isn't the main choice. This skill is an interaction recipe, not an existing code component.

Part of the sixteen-effect motion set (45–60), inspired by the Douyin video 「非程序员AI开发必看教程：16种常见动画效果科普」 by 大锤和AI. Specs, prompts and demo are written for this library. Timing and easing follow 45 Easing & Timing.

## Interaction contract

- Input: none; it loops on its own while visible.
- States: running, paused (off screen, hidden tab, or by the user), static (reduced motion).
- Cancellation and edge cases: pauses when off screen; corner radius of the beam matches the card; works at any card size.
- Accessibility: decorative; the card's importance is also stated in text (a 'Recommended' tag). Because it loops for more than 5 seconds, provide a way to pause it or let it stop after a few loops (WCAG 2.2.2).
- Reduced motion: a static gradient border instead of the moving beam.

## Implementation notes

- Register the angle: `@property --beam { syntax: '<angle>'; initial-value: 0deg; inherits: false }`.
- On `::before` (inset -1.5px, `border-radius: inherit`, padding 1.5px): `background: conic-gradient(from var(--beam), transparent 0 68%, accent 80%, white 86%, accent-2 90%, transparent 96%)`; mask it to the border with `mask: linear-gradient(#000 0 0) content-box exclude, linear-gradient(#000 0 0)` (plus the `-webkit-mask-composite: xor` version).
- `animation: beam 3.5s linear infinite` with `@keyframes beam { to { --beam: 360deg } }`; add a soft outer glow on `::after`.
- Fallback for browsers without `@property`: animate rotation of an oversized gradient behind a clipped card.
- Avoid: more than one beam per screen, fast loops (under 2s), and thick beams.

## Acceptance criteria

1. A short arc travels around a 1–2px border once every 3–4s, linear, with matching corner radius.
2. Only one element per screen has it, and its meaning is also given in text.
3. It pauses off screen and can be paused by the user.
4. Works with mouse, touch and keyboard as described in the interaction contract.
5. Reduced-motion mode presents the same information without the movement described above.
6. Only `transform`, `opacity`, `filter`, colour and shadow animate; no layout thrash; smooth on a mid-range phone.
7. No console errors or leaks; listeners, observers, timers and animation frames are cleaned up.
8. Responsive at 375px, 768px and 1440px.

## Prompt terms

| English prompt line | 中文提示詞 |
| --- | --- |
| Add a Border Beam to the recommended plan card: a short bright arc travelling around its 1.5px border every 3.5 seconds; no other card gets it. | 給推薦套餐卡片加邊緣流光（Border Beam）：一小段亮光沿 1.5px 邊框循環流動，3.5 秒一圈，其他卡片不加。 |

## Copy-ready English prompt

```text
Add a border beam to the recommended card only. Register @property --beam as an angle. On the card's ::before (inset -1.5px, padding 1.5px, border-radius inherit, pointer-events none), use conic-gradient(from var(--beam), transparent 0 68%, accent 80%, white 86%, accent-2 90%, transparent 96%) masked to the border with mask-composite exclude (and -webkit-mask-composite xor). Animate --beam from 0 to 360deg over 3.5s linear infinite, add a soft outer glow, pause when off screen, and provide a pause control. The card also carries a visible 'Recommended' tag. Under prefers-reduced-motion use a static gradient border.
```
