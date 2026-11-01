---
name: ui-41-ascii-sharks
description: Use when a hero or section should have a living ASCII ocean behind it, with fish schools and sharks that hunt, scatter from the cursor and splash on tap. ASCII Sharks (ASCII 鯊魚海洋) recipe built on the MIT ascii-sharks engine, with readability, reduced-motion and cleanup rules.
---
# UI-41 — ASCII 鯊魚海洋 / ASCII Sharks

**Category:** 氛圍與吸睛 / Ambient & Attention

## Effect

A dark canvas filled with fish and sharks drawn entirely from monospace characters. Schools swirl and drift, sharks cruise through and pick off stragglers, and the whole school bolts when one is close. Fish shy away from the mouse, and a click or tap sends out a splash. It reads as retro terminal art but moves like a nature documentary.

## When to use

Use behind a landing-page hero, a 404 page, a launch teaser or a developer/AI-product page that wants personality. Not for content-dense pages, light-themed brands that can't take a black panel, or more than one per page. It is decoration: the headline and call to action must work without it.

Built on **ascii-sharks** by stackedlol — https://github.com/stackedlol/ascii-sharks (MIT). Checked 2026-11-02 at commit `a0074c1`. The engine already handles the loop, resize, off-screen pausing and reduced motion; this recipe covers how to place it in a page.

## Setup

The repo is not on npm. Copy its `src/` folder into your project (keep its `LICENSE` with it), or bundle it into one script:

```bash
git clone --depth 1 https://github.com/stackedlol/ascii-sharks.git
npx esbuild ascii-sharks/src/index.ts --bundle --format=iife --global-name=AsciiSharks --minify --outfile=ascii-sharks.min.js
```

Then:

```ts
import { OceanEngine } from "./ascii-sharks/src";   // or AsciiSharks.OceanEngine from the bundle
const engine = new OceanEngine(canvas, [{ kind: "hammerhead", size: 1 }, { kind: "mako", size: 0.8 }]);
// on unmount / page leave
engine.destroy();
```

React: `import { AsciiOcean } from "./ascii-sharks/src/react"` and render `<AsciiOcean className="ocean" sharks={[...]} />`.

Shark kinds: `classic`, `hammerhead`, `greathammer`, `zebra`, `tiger`, `mako`, `thresher`, `nurse`. `size` is relative to the biggest (1). Leave the list out for four classic sharks at different depths.

## Interaction contract

- Input: none to run. Mouse movement over the canvas makes nearby fish flee (touch does not, so a finger doesn't drag the school around). Click or tap makes a splash.
- States: running, paused off screen (automatic), still frame (reduced motion).
- Cancellation and edge cases: resizes with its box (ResizeObserver); the frame step is fixed at 60 Hz with a catch-up cap, so a slow device slows the sim instead of jumping; pointer state clears when the pointer leaves the window or it loses focus.
- Accessibility: the canvas is decorative — `aria-hidden="true"`, no focus, and nothing important lives inside it. Text on top needs a solid or scrimmed backing so contrast stays at 4.5:1 while glyphs swim behind it. Because the motion runs longer than 5 seconds, give a visible Pause control (WCAG 2.2.2): call `engine.destroy()` to stop and create a new engine to resume.
- Reduced motion: the engine lets the ocean settle for a few seconds, then draws one still frame and never animates; splashes are off.

## Implementation notes

- The canvas must have a real size from CSS (`display:block; width:100%; height:…`) before the engine starts; a 0×0 canvas is skipped until it gets one.
- Set the font on the canvas with CSS (`font-family: "Geist Mono", ui-monospace, Menlo, monospace`). The engine reads it, and redraws once the webfont loads. Any monospace face works; weight 600 reads best.
- The renderer paints its own black background. Put the canvas in a dark panel with rounded corners, or full-bleed behind a dark hero; don't try to tint it light.
- Layer text above it with `position:relative; z-index:1` and `pointer-events:none` on the overlay wrapper (re-enable on buttons), so the pointer still reaches the fish.
- Pick 2–4 sharks. More than that empties the schools quickly and looks chaotic.
- Avoid: running two engines on one page, leaving it running in a hidden tab panel without destroying it, or placing body text directly on the glyphs.

## Acceptance criteria

1. Fish schools and sharks animate smoothly; schools scatter when a shark approaches.
2. Moving the mouse over the canvas pushes fish away; clicking or tapping splashes.
3. Headline and buttons stay readable (4.5:1) and clickable on top of the ocean.
4. A visible Pause control stops all motion and Play resumes it.
5. Reduced-motion mode shows a single settled frame with no animation.
6. The canvas stops drawing when scrolled off screen; no console errors; `destroy()` removes every listener, observer and animation frame.
7. Responsive at 375px, 768px and 1440px.

## Prompt terms

| English prompt line | 中文提示詞 |
| --- | --- |
| Put an ASCII Sharks ocean behind the hero: monospace fish schools and sharks that hunt, flee the cursor and splash on tap, with a pause button. | 在主視覺後面放一片 ASCII 鯊魚海洋（ASCII Sharks）：用等寬字元畫的魚群和鯊魚會捕獵、躲開游標、點擊濺起水花，並提供暫停按鈕。 |

## Copy-ready English prompt

```text
Add an ASCII ocean behind the hero using the MIT ascii-sharks engine (github.com/stackedlol/ascii-sharks). Copy its src/ folder with its LICENSE into the project and create new OceanEngine(canvas, [{kind:"hammerhead",size:1},{kind:"mako",size:0.8},{kind:"classic",size:0.65}]). The canvas is aria-hidden, display:block, fills a dark rounded panel (min-height 70vh on desktop, 60vh on mobile), font-family "Geist Mono", ui-monospace, monospace. Overlay the headline and CTA on a translucent dark scrim with z-index above the canvas and pointer-events:none on the wrapper (auto on buttons). Add a visible Pause/Play button: pause calls engine.destroy(), play creates a new engine. Call destroy() on unmount. Leave reduced motion to the engine (it draws one still frame).
```
