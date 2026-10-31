---
name: 03-swipe-selection
description: Use when letting users pick one option from a horizontal swipeable set. Swipe Selection (滑動選擇) UI interaction recipe covering pointer, touch, keyboard, accessibility and reduced motion.
---
# 03 — 滑動選擇 / Swipe Selection

**Category:** 輸入與控制 / Inputs & Controls

## Effect

The user swipes through a horizontal set of options (cards, plans, colours, dates) and the item that settles in the centre becomes the selection. Neighbouring items stay partly visible to show there is more, and the selected item is clearly emphasised once it snaps into place.

## When to use

Use when letting users pick one option from a horizontal swipeable set. This skill is an interaction recipe, not an existing code component.

## Copy-ready English prompt

```text
Create a reusable swipe selection interaction for choosing one option from a horizontal set. Items scroll and snap to a centred position using native scroll snapping where possible, with neighbouring items partly visible as an affordance. The centred item becomes the selected value after the scroll settles, with a clear visual emphasis that does not rely on colour alone. Support touch swipe, trackpad and mouse drag, previous/next buttons, and keyboard (Arrow keys move one option, Home/End jump to the ends, Enter or Space confirms when selection requires confirmation). Expose the set as a radiogroup or listbox with an accessible name, announce the selected option and its position ("3 of 7"), and keep focus on the selected item. Distinguish a swipe from a vertical page scroll and from a tap on an item; tapping a non-centred item should scroll it into the centre. Define behaviour at both ends (bounded or looping), handle a single option, empty, loading and error states, and preserve the selection when items are re-rendered or the viewport resizes. With prefers-reduced-motion, jump between items without momentum or scale effects. Do not fire selection side effects during intermediate scroll positions; commit only once the scroll has settled.
```
