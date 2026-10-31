---
name: 63-remotion-shotcraft
description: "Use when Lillian asks for video-shotcraft or a cinematic product promo, demo or launch video of a website or app; renders MP4 with Remotion."
---

# 63 — Remotion Shotcraft (video-shotcraft)

**Category:** 技能庫 / Skill Library · 影片與媒體 / Video & Media

video-shotcraft turns a website/app into a cinematic product video with Remotion: real page screenshots, 2.5D camera moves, beat-synced cuts, SFX, 100+ shot recipe cards and the Ink Press template.
Source: https://github.com/Vincentwei1021/video-shotcraft (Apache-2.0). Tested 2026-10-21, commit 43bd349, Remotion 4.0.484.
Gallery of shot cards to pick from: https://vincentwei1021.github.io/video-shotcraft/

Best for: product promos (portfolio pieces, the 3PL returns app, AARVO Shop, Digital Cards). Not for Sena & Pudding reels or talking-head content — use their own skills.

## 1. Setup (every session — the workspace resets)

```bash
cd /tmp && git clone --depth 1 https://github.com/Vincentwei1021/video-shotcraft.git
cd video-shotcraft/template && npm ci
```

Then read the repo's own `SKILL.md` in full — it is the real instruction set (written in Chinese). Follow its mode choice: Ink Press template / autonomous free creation / co-creation, plus single-shot mode.

## 2. Gotchas found in testing (cloud workspace)

- **Browser:** the full Chromium fails (old headless removed). Use the headless shell:
  `--browser-executable=/opt/pw-browsers/chromium_headless_shell-*/chrome-linux/headless_shell.real` (glob it with `ls`).
- **Concurrency:** the template config sets 4; the workspace has 2 cores. Pass `--concurrency=2` or edit `remotion.config.ts`.
- Test: `npx remotion still src/index.ts AiflPromo out.png --frame=150 ...` before a full render.
- Real page captures need the product running locally or a reachable URL; non-GitHub sites may be blocked from the shell — ask Lillian for screenshots/recordings instead.
- Sensitive data (customer names, orders, keys) must be faked before capture.

## 3. Lillian's defaults

- Ask which mode if she hasn't said; recommend co-creation for portfolio pieces.
- Visual language comes from the product's own design tokens (the repo insists on this too).
- Deliver 16:9 1920×1080 by default; offer a 9:16 cut for reels.
- Bilingual captions when asked: Traditional Chinese (Noto Sans CJK TC) + English.

## 4. Verify before sending

`ffprobe -v error -show_entries format=duration:stream=width,height -of csv=p=0 out.mp4`, grab a frame with ffmpeg and look at it, then send the MP4.