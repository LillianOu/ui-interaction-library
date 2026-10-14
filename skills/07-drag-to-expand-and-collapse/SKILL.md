---
name: 07-drag-to-expand-and-collapse
description: Use when building a bottom sheet, drawer or panel that is dragged open and closed. Drag to Expand & Collapse (拖曳展開與收合) UI interaction recipe covering pointer, touch, keyboard, accessibility and reduced motion.
---
# 07 — 拖曳展開與收合 / Drag to Expand & Collapse

**Category:** 版面與導覽 / Layout & Navigation

## Effect

A panel such as a bottom sheet, side drawer or card can be pulled open or pushed closed by dragging its handle. It follows the finger, then snaps to the nearest defined height (collapsed, half or full) based on how far and how fast it was moved. Tapping the handle or a button does the same thing without dragging.

## When to use

Use when building a bottom sheet, drawer or panel that is dragged open and closed. This skill is an interaction recipe, not an existing code component.

## Copy-ready English prompt

```text
Create a reusable drag-to-expand-and-collapse panel, such as a bottom sheet, side drawer or expandable card, with defined snap points (for example collapsed, half and full). The panel follows the pointer or finger while dragging from a visible handle, then snaps to the nearest snap point using both distance and release velocity, with resistance beyond the first and last snap point. Do not hijack scrolling: when the panel contains scrollable content, only start dragging the panel when the content is scrolled to the top or the gesture starts on the handle. Provide non-drag alternatives: the handle is a button with aria-expanded that toggles or cycles states on click, tap, Enter or Space, and Escape collapses or closes the panel. When the panel opens as a modal, trap focus inside it, restore focus to the trigger on close, and make background content inert; when it is non-modal, keep focus order logical. Handle pointer cancel, orientation and viewport changes, on-screen keyboards, safe-area insets and content that changes height while open. Announce state changes through the accessible name and expanded state. With prefers-reduced-motion, jump directly to the target snap point. Keep the panel usable when JavaScript gestures fail by falling back to the button controls.
```
