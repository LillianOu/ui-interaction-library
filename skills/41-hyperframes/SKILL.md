---
name: 41-hyperframes
description: Use when you want an AI tool to make a video from web code (launch films, explainers, title cards, reels) and also find or generate the music, images and voiceover it needs. HyperFrames routes to HeyGen's official hyperframes, hyperframes-cli and media-use skills.
---
# 41 — HyperFrames Pack
**Category:** 技能庫 / Skill Library · 影片與媒體 / Video & Media
**Powered by:** [heygen-com/hyperframes](https://github.com/heygen-com/hyperframes) `hyperframes` · `hyperframes-cli` · `media-use` (Apache-2.0)

> This skill is a guide, not a copy. It explains when to call an external skill, how to install it and how to get good results. It contains none of the original skills' text; install the originals to use them.

## What it does

HyperFrames gathers the pieces and cuts the reel. HyperFrames renders an HTML page frame by frame into an MP4, so the same files always produce the same video. The three official skills are one team: one knows how to build the video, one knows the command-line tool, and one fetches or makes the media that goes in it.

## When to use

- Use for motion graphics, product and launch videos, stat cards, kinetic type and vertical reels built from code.
- Use when the video needs music, sound effects, stock images, logos, voiceover or captions sourced for it.
- Do not use for scroll or hover animation on a live web page. Call 32 GSAP Skills or the motion skills 09–13.

## Routing

The three come as a set: install all three together.

| Job | Call | What it covers |
| --- | --- | --- |
| Build or edit a video | `hyperframes` | The rules a composition must follow and the build-check-render loop; read first |
| Run the tool | `hyperframes-cli` | Commands by job: create a project, check it, look at frames, edit the timeline, render and publish |
| Get the media | `media-use` | Finds or generates music, sound, images, icons, logos, voiceover and transcripts, and logs where each came from |

## Install

```bash
npx hyperframes skills update        # installs the core set from the latest main
# or
npx skills add heygen-com/hyperframes
```

Requirements: Node.js 22+ and FFmpeg; rendering uses a headless Chromium. Some `media-use` sources need a HeyGen sign-in or credits; free and local options are listed in the skill.

## How to ask

- "Ask HyperFrames to make a 15-second vertical reel announcing the new collection, with music."
- "HyperFrames, turn this landing page into a 30-second launch film."

## Watch-outs

- **Overlaps with 62 HyperFrames Video** in this library, which wraps the same tool. Use these official skills when you want the newest features and media sourcing; keep 62 HyperFrames Video for the tested house workflow. Do not load both in one session.
- The older `html-to-video` skill is an earlier copy of 62 HyperFrames Video. Remove it if it is still installed.
- Check the licence the media ledger records before publishing; Creative Commons sounds may need a credit line.
- Render a draft first; full-quality renders are slow.

## Credit

`hyperframes`, `hyperframes-cli` and `media-use` by HeyGen, Apache-2.0. Checked on 2026-10-31 at commit `164d6c7`.

## Copy-ready English prompt

```text
Use the hyperframes skills to make a <length>-second <aspect ratio> video about <subject>. Use media-use for music and any images, and log their sources. Run the check before rendering, render a draft first, and show me frames at the key moments.
```
