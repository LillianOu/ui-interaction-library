---
name: 44-studio-otter-openfilm
description: Use when you want a coding agent to make a video you can then fix by hand in a real editor (launch films, explainers, lyric videos, demos, recaps), or to cut, check, render or export a film for Premiere, Final Cut or DaVinci. Studio Otter routes to the official openfilm skill and the film styles it carries.
---
# 44 — 水獺片場師 / Studio Otter (OpenFilm)

**Category:** 開發與工作流工具組 / Dev & Workflow Toolkit
**Powered by:** [openfilm/openfilm](https://github.com/openfilm/openfilm) `openfilm` (MIT)

> A crew member is a guide, not a copy. It explains when to call an external skill, how to install it and how to get good results. It contains none of the original skill's text; install the original to use it.

## What it does

Studio Otter directs the shoot and then hands you the edit. With OpenFilm, the agent writes a film as a folder: one `film.html` lays clips on tracks like a timeline, and every animated shot is an ordinary web page that can draw any moment of itself. Studio, a local editor in your browser, plays the film as it is built, and lets you move, restyle and retype anything in a shot, or trim and recut clips, without asking the agent again. Your edits are saved back to the files, so the agent keeps them on its next pass.

## When to use

- Use when you want to make the video with an agent but finish it yourself, by eye, in an editor.
- Use for a ready-made film style: keynote launch, premium motion graphics, cut-paper collage, whiteboard explainer, lyric video, vintage-film memories, screen-recording demos, presenter-in-a-window talks, long video to vertical shorts, or remaking a reference video.
- Use when the cut must go on into Premiere Pro, Final Cut Pro or DaVinci Resolve, or when you need stems, subtitles, a GIF, stills or a transparent video.
- Do not use for scroll or hover animation on a live web page. Call 32 Swift Swallow or the motion skills 09–14.
- Do not use for a quick code-only reel with sourced media in the house workflow. Call 41 Reel Raccoon (HyperFrames).

## Routing

One skill to install; the styles come inside it.

| Job | Call | What it covers |
| --- | --- | --- |
| Make, edit, check or render a film | `openfilm` | Points the agent at the manual the tool prints, which is the whole rulebook; read first |
| Pick a film style | `openfilm skills`, then `openfilm skill <name>` | Lists the styles that ship with the tool and prints one for the agent to follow: `keynote`, `motion-graphics`, `collage`, `whiteboard`, `lyric-video`, `vintage-film`, `screen-demo`, `presenter-pip`, `long-to-short`, `replicate` |
| See a film and fix it | `openfilm open` | Opens Studio on a new, existing or GitHub-hosted film |
| Check before trusting | `openfilm look` | Contact sheet, single frames or a range; flags frames that change between renders, page errors, failed fonts, missing sounds and clipped text |
| Get voice, music, images, footage | `openfilm get` | Only works for services you have connected with your own keys |
| Export the MP4 | `openfilm render` | Options for 4K, motion blur and transparent video |

## Install

```bash
npx skills add openfilm/openfilm
```

Or use the desktop app for macOS or Windows from [openfilm.dev](https://openfilm.dev): Studio with a chat panel for Claude Code, Codex or its own agent, with ffmpeg and the browser bundled.

Requirements: Node.js 22.2+ and FFmpeg, plus git for saved versions; the first run downloads a headless Chromium (about 100 MB). Preview in a Chromium browser (Chrome, Edge) so what you see is what exports. No account is needed to make, edit or render. Generated voice, music, images and video need your own keys (ElevenLabs, OpenAI, Google, fal and others) in Studio → Settings → Providers, and those services bill you.

## How to ask

- "Ask Studio Otter to make a 20-second keynote-style launch film for Returns Bench, then open it in Studio."
- "Studio Otter, turn this screen recording into a tutorial with the view following my clicks."
- "Studio Otter, cut this 40-minute talk into five vertical shorts with subtitles."

## Watch-outs

- **Overlaps with 41 Reel Raccoon and Flip Fox (HyperFrames), and with Director Crane (Remotion).** All make video from web code. Pick Studio Otter when you will edit by hand or need an NLE handoff; pick Reel Raccoon or Flip Fox for the tested HyperFrames workflow; pick Director Crane for its shot-by-shot product promos. Load one video skill per session so agents do not mix formats.
- Very new: launched in October 2026 and patching daily (0.1.x). Pin a version for client work and re-run `openfilm doctor` after updates.
- The one rule every shot must keep: the same moment always draws the same picture. Shots that rely on timers, random values or live data will flicker or differ between renders; `look` is how you catch it.
- Generated video clips are the expensive part; Studio asks you to confirm each one. Check every generated asset's licence before publishing.
- Subtitles come from `.vtt` files next to each sound, not drawn into the picture; edit them in Studio.
- The code is MIT but the OpenFilm name and logo are trademarks: "made with OpenFilm" is fine; naming your own product or fork "OpenFilm", or using its logo, is not.

## Credit

`openfilm` by the OpenFilm contributors, MIT. Checked on 2026-10-31 at commit `b7673b5`.

## Copy-ready English prompt

```text
Use the openfilm skill to make a <length>-second <aspect ratio> film about <subject>. Run `openfilm skills` and use the <style> style if it fits. Open it in Studio while you build so I can watch. Run `openfilm look` and fix every issue it names before rendering. Keep any edits I make in Studio. Render a draft first, and tell me which services I need to connect for voice or music.
```
