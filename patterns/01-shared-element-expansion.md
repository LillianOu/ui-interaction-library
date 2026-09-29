# 01 — 共享元素展開 / Shared Element Expansion

## Effect

An item visually carries its identity into a detail view, expanding from its original position rather than appearing as an unrelated new screen. Preserve spatial context and return the item to its source on close.

## Copy-ready English prompt

```text
Create a reusable shared-element expansion interaction. When a user opens an item, animate its representative visual and key metadata from the source card into the destination detail view while preserving logical focus and source context. Support mouse, touch, keyboard activation, Escape/back dismissal, reduced motion, interrupted transitions, loading and failed states. Do not rely on animation alone to communicate the new state; use semantic structure, accessible labels, visible focus, and a stable fallback when the source item is no longer available.
```
