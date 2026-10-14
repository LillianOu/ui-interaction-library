---
name: hover-door-bloom
description: Build hover-triggered door bloom interaction for accessible interactive websites.
---
# Hover-triggered Door Bloom Interaction

## When to use
Use when the user requests hovering or focusing on an interactive door or panel. This skill is an implementation recipe, not an existing code component.

## Visual goal
A door/panel swings open, revealing content with an expanding floral or particle bloom.

## Interaction contract
- Input: pointerenter, focus, click/tap to toggle, Escape to close.
- Output: visually clear start, transition and final state. Specify duration/easing, layering, camera direction and exit behaviour before coding.
- Tap toggles the door; keyboard activation works; content remains navigable.
- Support prefers-reduced-motion: reduce with a static or crossfade alternative.

## Implementation
Use transform-origin, perspective and CSS transforms; animate reveal content independently; prefer buttons for controls.
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
“Implement Hover-triggered Door Bloom Interaction in a React + TypeScript page. A door/panel swings open, revealing content with an expanding floral or particle bloom. Tap toggles the door; keyboard activation works; content remains navigable. Provide editable parameters, reduced-motion fallback, and explain how to integrate the component.”
