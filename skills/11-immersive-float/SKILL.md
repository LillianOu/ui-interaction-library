---
name: 11-immersive-float
description: Use when building immersive float for an interactive website. Motion effect recipe for React + TypeScript with reduced-motion and touch fallbacks.
---
# 11 — 沉浸式漂浮 / Immersive Float

**Category:** 氛圍與吸睛 / Ambient & Attention

## When to use
Use when the user requests activating a floating immersive object. This skill is an implementation recipe, not an existing code component.

## Visual goal
An object drops or floats into a scene and triggers a bloom of foliage, particles, or other secondary elements.

## Interaction contract
- Input: click, tap, Enter or Space on an accessible activation control.
- Output: visually clear start, transition and final state. Specify duration/easing, layering, camera direction and exit behaviour before coding.
- Allow tap to trigger; ensure focus visibility and a restart control.
- Support prefers-reduced-motion: reduce with a static or crossfade alternative.

## Implementation
Use timeline-based transforms and opacity; stagger secondary elements; keep object and background on independent layers.
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
“Implement Immersive Float in a React + TypeScript page. An object drops or floats into a scene and triggers a bloom of foliage, particles, or other secondary elements. Allow tap to trigger; ensure focus visibility and a restart control. Provide editable parameters, reduced-motion fallback, and explain how to integrate the component.”
