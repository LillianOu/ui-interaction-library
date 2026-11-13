---
name: design-15-motion-prompt
description: Use when you know the look or movement you want but not its name (motion-graphics move, camera move, transition, UI part, landing-page effect, photo look or art style) and want to pick it from a numbered gallery of live samples, then have the AI build exactly that. Routes to showheyohtaki's motion-prompt skill.
---
# Design-15 — Motion Prompt

**Category:** 工具庫 / Tool Library · 設計 / Design
**Powered by:** [showheyohtaki/motion-prompt](https://github.com/showheyohtaki/motion-prompt) `motion-prompt` (MIT: free to use, change and share, including commercially, as long as the licence notice is kept)
**Gallery:** https://showheyohtaki.github.io/motion-prompt/

> This skill is a guide, not a copy. It explains when to call an external skill, how to install it and how to get good results. It contains none of the original skill's text; install the original to use it.

## What it does

Motion Prompt is a dictionary of names for the things you ask an AI to make. Every entry has a three-digit number (`#012`), a name, a one-line meaning, an example of how to ask for it and a looping live sample. When this guide was checked it held nine packs of 24 names (216 in all): motion-graphics moves (two packs), camera moves and transitions (two packs), UI component names, landing-page and web effects (two packs), photo looks and lighting, and art styles for image generation. New packs keep being added.

The skill turns the gallery into a picker: the AI opens it, you tick the samples you like and send them back, and the AI rebuilds those exact moves in your project (Canvas, Remotion, CSS/SVG, Lottie or After Effects) with the published timing and easing, or turns them into prompts for a video or image model. You can also just give it numbers.

## When to use

- Use when you can picture a move but cannot name it ("the text that unscrambles", "the camera that pushes in").
- Use to choose openings, transitions and title moves for reels, ads and product videos, then hand them to the video tool.
- Use to name a landing-page effect or UI part precisely before asking Lovable, Bolt, v0 or Claude to build it.
- Use to choose a photo look, lighting or art style for an image-generation prompt.
- Do not use for the motion rules of an interface (easing, duration, stagger). Use UI-25 Easing & Timing and the UI Library Motion entries.
- Do not use to render the final video. Pick names here, then build with Video-01 HyperFrames Video or Video-04 Remotion Shotcraft.
- Do not use for a full page's visual direction. Use Design-03 Taste Pack.

## Routing

| Job | Call | Why |
| --- | --- | --- |
| Don't know the name, want to browse and pick | `motion-prompt` → "open the library" | Opens the gallery; your ticks come back to the AI |
| Know the number | `motion-prompt` → "use #012 and #045" | Pulls the spec and code for those entries |
| Describe it in words | `motion-prompt` → "find a typewriter text effect" | Searches the catalogue in English or Japanese |
| Video model or image model prompt | `motion-prompt` → "write a prompt for #102" | Gives the ready-made prompt for that entry |
| No install at all | The gallery or `packs/` name lists | Copy the name into any AI, video model or brief |

## Install

**Claude app (claude.ai or Claude desktop, no Terminal):** download the repo as a ZIP from [showheyohtaki/motion-prompt](https://github.com/showheyohtaki/motion-prompt) (green Code button → Download ZIP), zip only the `skills/motion-prompt` folder, upload it in Settings → Skills and switch it on. Code execution must be on. In the Claude app the AI can't open a browser on your computer, so open the gallery yourself, pick, and paste your picks or the numbers into the chat.

**Claude Code (plugin):**

```text
/plugin marketplace add showheyohtaki/motion-prompt
/plugin install motion-prompt@motion-prompt
```

**Claude Code, Codex and other agents (one command):**

```bash
npx skills add showheyohtaki/motion-prompt
```

Requirements: Node.js 18 or later for the skill's catalogue script, and internet access to the gallery (it reads the latest catalogue each time). The browser picker needs Claude Code or Codex running on your own computer.

## How to ask

- "Open the motion-prompt library." (tick samples, add a note like "for the opening title", press Send to AI)
- "Use #129 Text scramble for the headline and #137 Push transition between scenes."
- "Open the library filtered to camera moves."
- "Find a reveal for the logo, then build it in Remotion."
- "Give me the image prompt for the art style I picked."

## Watch-outs

- The numbers belong to Motion Prompt, not to this library. "#012" means Motion Prompt #012, not UI-12.
- Samples are simple flat illustrations that show the movement. Your brand colours, fonts and footage still have to be applied; say so in the prompt.
- Packs are added often, so counts and numbers above may be out of date. Ask the skill to list packs rather than relying on this page.
- Overlaps with video tools: pick here, build there. Running two video skills in one session can confuse the agent.
- Name lists exist in English, Japanese, Spanish and both Simplified and Traditional Chinese; the gallery itself is English and Japanese.

## Credit

Original work by Shohei Ohtaki, MIT. Checked on 2026-11-13 at commit `da14d9c`.

## Copy-ready English prompt

```text
Use the motion-prompt skill. Open the library so I can pick, then rebuild my picks in this project with the published timing and easing, using my brand colours and fonts.
```
