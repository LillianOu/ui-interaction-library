---
name: design-16-pixel2motion
description: Use when you have a logo as a PNG, JPG, WebP or screenshot and want it rebuilt as a clean SVG and animated into a logo reveal, splash screen, brand intro or loading mark, delivered as HTML with GIF or video previews. Routes to nolangz's pixel2motion skill.
---
# Design-16 — Pixel2Motion

**Category:** 工具庫 / Tool Library · 設計 / Design
**Powered by:** [nolangz/pixel2motion](https://github.com/nolangz/pixel2motion) `pixel2motion` (MIT: free to use, change and share, including commercially, as long as the licence notice is kept)
**Live demo:** https://nolangz.github.io/pixel2motion/

> This skill is a guide, not a copy. It explains when to call an external skill, how to install it and how to get good results. It contains none of the original skill's text; install the original to use it.

## What it does

Pixel2Motion takes a flat logo image and works in two halves. First it redraws the logo as a simple, smooth SVG with as few shapes as possible, and checks the redraw against the original image so you can see how close it is. Then it animates that SVG into a short, choreographed reveal, and the last frame always lands exactly on the checked static logo. You get a standalone HTML page of the animation, GIF or video previews, and evidence that the motion is smooth (easing and continuity checks).

## When to use

- Use to turn a brand logo (AARVO, AARVO Shop, VinoIQ, a client mark) into an animated intro, splash screen or loading mark.
- Use when you only have a raster logo and need a clean, editable SVG of it as well.
- Use to give a portfolio case study a logo reveal you can embed on the web.
- Do not use for full videos with scenes, music or captions. Export the logo animation here, then place it in Video-01 HyperFrames Video or Video-04 Remotion Shotcraft.
- Do not use to choose the name of a move. Use Design-15 Motion Prompt first, then ask Pixel2Motion for that style.
- Do not use for complex illustrations or photos; it is built for logos and marks.

## Routing

| Job | Call | Why |
| --- | --- | --- |
| Logo image → animated reveal | `pixel2motion` → "animate this logo" | Runs the full vectorise-then-animate workflow |
| Logo image → clean SVG only | `pixel2motion` → "vectorise this logo, no animation" | Stops after the checked SVG |
| Existing SVG → motion | `pixel2motion` → "animate this SVG" | Skips the redraw step |
| Hover, idle or loading loop | `pixel2motion` → "make a hover / idle loop for this mark" | Short looping motion instead of a one-off reveal |

## Install

**Claude Code, Codex and other agents:**

```bash
npx skills add nolangz/pixel2motion
```

Or download the repo as a ZIP and copy the whole folder (with `SKILL.md`, `scripts/` and `references/`) into your agent's skills folder.

**Claude app (no Terminal):** zip the repo folder, upload it in Settings → Skills and switch it on. Code execution must be on.

Requirements: Python 3.10+ with Pillow, NumPy and Playwright, plus Chrome or Chromium for rendering. If Chrome is not found, set `CHROME_BIN` to its path.

## How to ask

- "Use pixel2motion on this PNG logo. Build a 2-second reveal for a website intro and give me the HTML and a GIF preview."
- "Vectorise this logo and show me the overlay against the original before animating."
- "Make a calm idle loop for this mark for the AARVO loading screen."

## Watch-outs

- Give it the cleanest, largest logo file you have; blurry or tiny sources give weaker SVGs.
- Check the overlay of the SVG against the original before approving the motion. The animation is only as good as the redraw.
- Brand colours come from the source image; say so if they should change.
- The author also offers a paid commercial service on pixel2motion.com. The open-source skill is what this guide covers.

## Credit

Original work by Nolan Lai (nolangz), MIT. Checked on 2026-11-17 at commit `e9faedb`.

## Copy-ready English prompt

```text
Use the pixel2motion skill on the attached logo. Rebuild it as a clean, minimal SVG, show me the overlay against the original, then animate it into a <length>-second <reveal / loop> for <use>. Deliver the HTML, a GIF preview and the motion check results.
```
