---
name: video-06-story-to-handdrawn-video
description: Use when a Chinese story, or a set of ordered illustration pages, should become a silent vertical hand-drawn animation (picture-book or illustrated-diary style) ready for voiceover and music. Routes to gnipbao's story-to-handdrawn-video skill and its Remotion renderer.
---
# Video-06 — story-to-handdrawn-video

**Category:** 工具庫 / Tool Library · 影片與媒體 / Video & Media
**Powered by:** [gnipbao/story-to-handdrawn-video](https://github.com/gnipbao/story-to-handdrawn-video) `story-to-handdrawn-video` (MIT: free to use, change and share, including commercially, as long as the licence notice is kept)
**Style library:** https://story-handdrawn-style-library.vercel.app

> This skill is a guide, not a copy. It explains when to call an external skill, how to install it and how to get good results. It contains none of the original skill's text; install the original to use it.

## What it does

You give it a short story in Chinese, or a folder of pages in order, and it makes a 3:4 vertical hand-drawn video. The agent splits the story into beats (one full sentence per beat by default), keeps your wording, draws each page with the handwritten Chinese caption inside the art, then animates each page from lettering to black-and-white sketch to full colour. A page-flip mode turns whole pages like a book instead. The default look is a coloured-pencil illustrated diary; a style library of a few hundred recipes and 30 palettes lets you pick another, or match the look of a reference image and save it for reuse. The export is a silent H.264 video (720×960 or 1080×1440) for you to add voice and music to afterwards.

## When to use

- Use for AARVO KIDS picture-book stories, bedtime stories and illustrated-diary shorts in Chinese.
- Use to animate pages you already illustrated, in order, with a page-flip or layered reveal.
- Use to keep one character and one art style steady across every page of a story.
- Do not use for English captions; it is built around Chinese lettering. For English kids' reels use Video-05 Sena & Pudding Reel Builder or Video-01 HyperFrames Video.
- Do not use for product promos. Use Video-04 Remotion Shotcraft.
- Do not use when the final video needs sound inside it; add voiceover and music in CapCut afterwards.

## Routing

| Job | Call | Why |
| --- | --- | --- |
| Story text → hand-drawn video | `story-to-handdrawn-video` → "make this story into a hand-drawn animation, preview first" | Full workflow: beats, pages, animation, render |
| Pick a look first | The online style library, then name the style ID in the prompt | Compare styles on the same sample scene |
| Your own pages → video | `story-to-handdrawn-video` → "turn these images into a page-flip animation, in order" | Skips image generation |
| Match a reference image | `story-to-handdrawn-video` → "use the style of this reference and save it" | Analyses the reference and keeps it for next time |

## Install

It has two parts: the renderer project and the skill. Install both.

```bash
git clone https://github.com/gnipbao/story-to-handdrawn-video.git
cd story-to-handdrawn-video
npm ci
npm run check
cp -R skill-package/story-to-handdrawn-video ~/.claude/skills/
```

If you call it from outside the project folder, set `STORY_VIDEO_PROJECT` to the project's full path.

Requirements: Node.js 20+, Python 3.10+, FFmpeg (with ffprobe), npm and Chrome. Making new artwork also needs an image-generation tool the agent can call; without one, use your own pages.

## How to ask

Prompts work best in Chinese, for example:

- 「使用 story-to-handdrawn-video，把下面的故事做成手繪動畫，先給我預覽版：……」
- 「用 HS-128 四季旅行水彩風格，標題叫〈紙上的夏天〉，先出預覽。」
- 「按順序把這些圖片做成翻書動畫。」

## Watch-outs

- Always ask for a preview first; full renders and image generation take time and credits.
- Check every page's handwritten Chinese for wrong characters before the final render.
- Small identifying details (a mole, a broken umbrella rib) can get lost at page size. Make key props big and clear in the story.
- If you want Traditional Chinese captions, say so in the prompt and check the result.
- It renders with Remotion. Remotion has its own licence: free for individuals and very small companies, a paid company licence above that. Check before using it for client work.

## Credit

Original work by gnipbao, MIT. Checked on 2026-11-17 at commit `198aefa`.

## Copy-ready English prompt

```text
Use the story-to-handdrawn-video skill. Turn the story below into a silent 3:4 hand-drawn animation in the <style ID or name> style, title "<title>". Keep my wording, keep the main character consistent on every page, and give me a preview render first.
```
