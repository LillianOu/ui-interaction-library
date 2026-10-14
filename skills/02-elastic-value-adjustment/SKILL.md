---
name: 02-elastic-value-adjustment
description: Use when building a draggable or scrubbable numeric control such as quantity, size or volume. Elastic Value Adjustment (彈性數值調節) UI interaction recipe covering pointer, touch, keyboard, accessibility and reduced motion.
---
# 02 — 彈性數值調節 / Elastic Value Adjustment

**Category:** 輸入與控制 / Input & Controls

## Effect

A numeric value is changed by dragging, scrubbing or pressing, and the control responds with a soft, spring-like give that makes the value feel physical. Pulling past the minimum or maximum stretches slightly and settles back, so the user feels the boundary instead of hitting a dead stop. The current value stays readable and exact at all times.

## When to use

Use when building a draggable or scrubbable numeric control such as quantity, size or volume. This skill is an interaction recipe, not an existing code component.

## Copy-ready English prompt

```text
Create a reusable elastic value adjustment control for numbers such as quantity, size, volume or price. Let the user change the value by horizontal or vertical drag, touch scrub, mouse wheel, increment/decrement buttons and keyboard (Arrow keys for one step, Shift+Arrow or Page Up/Down for larger steps, Home/End for min/max). Apply a damped spring response while dragging and an elastic overscroll when the user pulls beyond min or max, then settle back to the nearest valid value on release. Snap to a defined step and show the exact value in a live, readable label; never let the animation display a value that will not be committed. Expose the control with role="spinbutton" or a native range/number input, with aria-valuemin, aria-valuemax, aria-valuenow and a human-readable aria-valuetext including units. Support Escape or pointer cancel to restore the value from before the gesture, prevent page scroll while a drag is active, and handle pointer capture loss. With prefers-reduced-motion, remove the spring and overscroll and update the value directly. Handle disabled, read-only, invalid and saving states, debounce expensive updates, and keep a plain text input fallback for typing an exact number.
```
