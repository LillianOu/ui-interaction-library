---
name: cursor-luminous-flow
description: Build cursor-driven luminous flow for accessible interactive websites.
---
# Cursor-driven Luminous Flow

## When to use
Use when the user requests pointer movement over an atmospheric scene. This skill is an implementation recipe, not an existing code component.

## Visual goal
A cursor-controlled luminous trail with soft volumetric-looking glow, parallax and damped motion.

## Interaction contract
- Input: pointermove and pointerleave on the interactive container; pointer coordinates normalized to [-1,1].
- Output: visually clear start, transition and final state. Specify duration/easing, layering, camera direction and exit behaviour before coding.
- On touch, use a slow ambient loop or drag interaction; never require hover.
- Support prefers-reduced-motion: reduce with a static or crossfade alternative.

## Implementation
Use CSS gradients and transforms for a lightweight default; optionally Three.js shaders for a true volumetric version.
- React + TypeScript: isolate the scene in a component, use refs, clean up listeners/animation frames and support resizing.
- Use GSAP only if the timeline complexity justifies it; scope animations and revert on unmount.
- Use original or properly licensed media. Do not copy the reference site's assets.

## Acceptance criteria
1. Runs without console errors or memory leaks.
2. Works with mouse, touch and keyboard where applicable.
3. Reduced-motion mode presents the same information without intensive motion.
4. Maintains readable contrast and does not trap scrolling or focus.
5. Responsive at 375px, 768px and 1440px; test on a real mobile browser.
6. Document adjustable speed, intensity, colors, assets and fallbacks.

## Suggested prompt
“Implement Cursor-driven Luminous Flow in a React + TypeScript page. A cursor-controlled luminous trail with soft volumetric-looking glow, parallax and damped motion. On touch, use a slow ambient loop or drag interaction; never require hover. Provide editable parameters, reduced-motion fallback, and explain how to integrate the component.”
