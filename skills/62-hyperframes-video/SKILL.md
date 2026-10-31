---
name: 62-hyperframes-video
description: "Use when Lillian asks for a video, reel, animated card, motion graphic or title sequence made from HTML, or mentions hyperframes; renders an MP4 by script."
---

# 62 — HyperFrames Video

**Category:** 技能庫 / Skill Library · 影片與媒體 / Video & Media

HyperFrames turns an HTML page with a paused GSAP timeline into a deterministic MP4.
Source: https://github.com/heygen-com/hyperframes (Apache-2.0). Tested 2026-10-12 with CLI 0.8.149, commit 86521b9.
Lillian's tested house workflow. The official HyperFrames skills are covered by 41 HyperFrames.

## 1. Setup (every session — the workspace resets)

```bash
node -v                      # needs 22+
which ffmpeg                 # needed for encoding
npx -y hyperframes@latest init <project> --non-interactive
cd <project>
```

Rendering needs a Chromium. If `render` says no browser is found, point it at one that exists:

```bash
find / -name chrome -type f -perm -u+x 2>/dev/null | grep -v proc | head -1
export HYPERFRAMES_BROWSER_PATH=<that path>   # e.g. /opt/pw-browsers/chromium-*/chrome-linux/chrome
```

The project's own CLAUDE.md lists the official HyperFrames skills (`/hyperframes`, `/motion-graphics`, `/hyperframes-core`…). For anything beyond a simple card, install them: `npx hyperframes skills update`, then read `/hyperframes` first.

## 2. Gotchas found in testing

- **CDNs may be blocked** (jsdelivr, Google Fonts). Install locally instead: `npm i gsap` and reference `./gsap.min.js` copied from `node_modules/gsap/dist/`.
- **Chinese text needs explicit `@font-face`**, or lint errors and the render falls back. Use system fonts with `local()`, one face per weight:
  ```css
  @font-face { font-family: 'Noto Sans CJK TC'; src: local('Noto Sans CJK TC'); font-weight: 400; }
  @font-face { font-family: 'Noto Sans CJK TC'; src: local('Noto Sans CJK TC Medium'); font-weight: 500; }
  @font-face { font-family: 'Noto Sans CJK TC'; src: local('Noto Sans CJK TC Black'); font-weight: 900; }
  ```
  A single `font-weight: 100 900` range face renders everything at regular weight.
- Always declare `window.__timelines = window.__timelines || {};` before registering the root timeline.
- No `Date.now()`, `Math.random()` or network fetches — renders must be deterministic.

## 3. Lillian's defaults

- Vertical reels: `data-width="1080" data-height="1920"`, viewport meta and body size to match.
- Bilingual: Traditional Chinese (Noto Sans CJK TC) + English; monospace for repo names/dates.
- Dark, premium, minimal; one accent colour per piece.
- For stat or ranking cards, build a ranked card with count-up and progress bar (see 57 Count Up for the number motion).

## 4. Loop

1. Write `index.html` (root `#root` with `data-composition-id`, `data-start`, `data-duration`, size; timed elements get `class="clip"` + `data-start` + `data-duration`).
2. `npx hyperframes lint` — fix every error.
3. `npx hyperframes render --quality draft --output draft.mp4` while iterating; `--quality looks` for review; `--quality delivery` for final.
4. Verify: `ffprobe -v error -show_entries format=duration:stream=width,height -of csv=p=0 out.mp4`, and grab a frame (`ffmpeg -ss <t> -i out.mp4 -frames:v 1 frame.png`) to look at before sending.
5. Send the MP4 to Lillian.