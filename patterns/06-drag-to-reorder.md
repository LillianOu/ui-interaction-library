# 06 — 拖曳排序 / Drag to Reorder

## Effect

The user picks up an item in a list or grid and drags it to a new position. The dragged item lifts above the others, and the remaining items slide aside to show where it will land. On release it settles into place and the new order is saved.

## Copy-ready English prompt

```text
Create a reusable drag-to-reorder interaction for vertical lists, horizontal lists and grids. Start a drag from a visible drag handle (or from a long press on touch) so normal clicks, taps, text selection and page scrolling still work. While dragging, lift the item with elevation, keep it under the pointer, and animate the other items to open a gap at the drop position. Auto-scroll the container when the pointer nears its edge. Provide a full keyboard alternative: focus the handle, press Space or Enter to pick up, Arrow keys to move, Space or Enter to drop, and Escape to cancel and return the item to its original place. Announce pick-up, each position change ("item 3 of 8, now position 5") and the drop through a live region, and offer optional "Move up" and "Move down" buttons for users who cannot drag. Handle pointer cancel, losing pointer capture, the item being removed or the list updating during a drag. Persist the new order only on drop, roll back visibly if saving fails, and keep a stable item identity rather than relying on indexes. With prefers-reduced-motion, move items without sliding animation. Respect disabled or locked items that cannot be moved or used as drop targets.
```
