---
name: 08-fly-to-target-feedback
description: Use when confirming add-to-cart, save or add-to-list actions with an item flying to its destination. Fly-to-Target Feedback (飛向目標的回饋) UI interaction recipe covering pointer, touch, keyboard, accessibility and reduced motion.
---
# 08 — 飛向目標的回饋 / Fly-to-Target Feedback

**Category:** 回饋與狀態 / Feedback & State

## Effect

After an action such as "Add to cart", "Save" or "Add to list", a small copy of the item flies along a short arc from where the user acted to the place where it now lives (a cart icon, a folder, a counter). The target then reacts with a brief pulse and an updated count, confirming where the item went.

## When to use

Use when confirming add-to-cart, save or add-to-list actions with an item flying to its destination. This skill is an interaction recipe, not an existing code component.

## Copy-ready English prompt

```text
Create a reusable fly-to-target feedback interaction. When the user completes an action like add to cart, save or add to collection, create a lightweight visual clone of the item (thumbnail or icon) at the source position and animate it along a short curved path to a target element such as a cart icon, folder or badge, scaling down as it travels. When it arrives, give the target a brief pulse and update its count or state. Treat the animation as decoration only: the real confirmation is the updated target and a polite live-region announcement such as "Added to cart, 3 items", and the action must not wait for the animation to finish. Compute source and target positions at runtime, and handle targets that are off-screen, hidden in a collapsed menu, inside a scrolled container, or not rendered; in those cases skip the flight and show an inline confirmation instead. Keep the clone out of the accessibility tree and ignore pointer events on it. Handle rapid repeated actions without stacking unlimited clones, and cancel or finish flights cleanly on navigation, resize or scroll. If the action fails, do not animate success; show an error near the source. With prefers-reduced-motion, skip the flight and update the target directly. Do not move keyboard focus to the target.
```
