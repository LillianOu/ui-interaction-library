---
name: scroll-helix-flow
description: Build scroll-driven helix flow for accessible interactive websites.
---
# Scroll-driven Helix Flow

## When to use
Use when the user requests scrolling through a spiralling helix. This skill is an implementation recipe, not an existing code component.

## Visual goal
A scroll-scrubbed helix rotating and translating through depth, with glowing strand highlights.

## Interaction contract
- Input: scroll progress of a bounded pinned section from 0 to 1.
- Output: visually clear start, transition and final state. Specify duration/easing, layering, camera direction and exit behaviour before coding.
- Provide static helix art or a simplified CSS version when WebGL is unavailable.
- Support prefers-reduced-motion: reduce with a static or crossfade alternative.

## Implementation
Use Three.js curves/tubes with GSAP ScrollTrigger or requestAnimationFrame; dispose GPU resources on unmount.
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
“Implement Scroll-driven Helix Flow in a React + TypeScript page. A scroll-scrubbed helix rotating and translating through depth, with glowing strand highlights. Provide static helix art or a simplified CSS version when WebGL is unavailable. Provide editable parameters, reduced-motion fallback, and explain how to integrate the component.”
