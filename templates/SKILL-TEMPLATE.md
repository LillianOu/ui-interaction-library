---
name: NN-kebab-case-name
description: Use when <the situation in which this interaction is the right choice>. <One short line on what it does.>
---
# NN — 中文名稱 / English Name

**Category:** <one category from CONTRIBUTING.md, e.g. 導覽與視圖 / Navigation & Views · 輸入與控制 / Inputs & Controls · 滾動動效 / Scroll · 游標與懸停 / Cursor & Hover>

## Effect

What the user sees and feels, in two or three sentences.

## When to use

Use when … This skill is an interaction recipe, not an existing code component.

## Interaction contract

- Input: mouse, touch, keyboard and any other triggers.
- States: idle, active, loading, success, error, disabled, empty, as relevant.
- Cancellation and edge cases: Escape, pointer cancel, interruption, resize, missing data.
- Accessibility: roles, labels, focus handling and announcements.
- Reduced motion: what replaces the animation.

## Implementation notes

Suggested techniques and libraries, and what to avoid.

## Acceptance criteria

1. Works with mouse, touch and keyboard.
2. Reduced-motion mode presents the same information without intensive motion.
3. No console errors or memory leaks; listeners and animation frames are cleaned up.
4. Responsive at 375px, 768px and 1440px.

## Copy-ready English prompt

```text
Create a reusable <interaction>. …
```
