---
name: 12-scroll-vortex-transit
description: Use when building scroll-driven vortex transit for an interactive website. Motion effect recipe for React + TypeScript with reduced-motion and touch fallbacks.
---
# 12 — 滾動漩渦轉場 / Scroll-driven Vortex Transit

**Category:** 動態視覺效果 / Motion Effects

## When to use
Use when the user requests scrolling through a depth-based vortex transition. This skill is an implementation recipe, not an existing code component.

## Visual goal
Text and objects orbit or rush past the camera, transitioning between content states.

## Interaction contract
- Input: scroll progress mapped to a bounded scene and timeline.
- Output: visually clear start, transition and final state. Specify duration/easing, layering, camera direction and exit behaviour before coding.
- Fallback to crossfade between content panels without motion.
- Support prefers-reduced-motion: reduce with a static or crossfade alternative.

## Implementation
Use CSS 3D transforms for typography; optional Three.js for particle tunnel; avoid heavy filters on large layers.
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
“Implement Scroll-driven Vortex Transit in a React + TypeScript page. Text and objects orbit or rush past the camera, transitioning between content states. Fallback to crossfade between content panels without motion. Provide editable parameters, reduced-motion fallback, and explain how to integrate the component.”
