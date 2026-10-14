# 04 — 動態狀態切換 / Animated State Transition

## Effect

A single control or element changes state (idle, loading, success, error; off and on; saved and unsaved) with a short morphing transition, so the user sees what changed in place rather than having content swap abruptly. The element keeps its position and size stable so the surrounding layout does not jump.

## Copy-ready English prompt

```text
Create a reusable animated state transition for a component that moves between defined states such as idle, loading, success, error and disabled (for example a submit button, toggle, status chip or save indicator). Define the states and allowed transitions explicitly as a small state machine, and animate only between valid states using shape, icon, colour and label changes that morph in place. Reserve stable dimensions so the surrounding layout does not shift. Communicate every state change in text as well as visually: update the accessible name or visible label, use aria-busy during loading, and announce success or error through a polite live region without moving focus. Keep the control operable by mouse, touch and keyboard, prevent duplicate actions while loading, and decide what happens if a new action arrives mid-transition (queue, cancel or ignore). Return from success to idle after a defined delay only if that does not hide information the user needs; errors should stay until dismissed or retried. With prefers-reduced-motion, switch states instantly or with a simple fade. Handle slow responses, timeouts, offline and failed requests, and make sure the final visible state always matches the real outcome rather than an optimistic guess that was never confirmed.
```
