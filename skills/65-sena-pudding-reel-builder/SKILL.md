---
name: 65-sena-pudding-reel-builder
description: "Use when Lillian asks to make, caption or rebuild a Sena & Pudding English reel (\"do episode 3\"); builds the finished video by script, not by clicking through CapCut."
---

# 65 — Sena & Pudding Reel Builder

**Category:** 技能庫 / Skill Library · 影片與媒體 / Video & Media

Vertical English-learning reels: Pudding (kitten, left) says a simple phrase, Sena (girl, right) says the polished version. One episode = four 15-second clips + end card, about 63 seconds. Lillian prepares the clips; this skill adds captions, hearts and music and writes the finished video.

**Keep token use low.** Do everything with shell commands on her computer. Do not drive CapCut with screenshots and clicks; that method costs many times more and was abandoned. Check results with one small contact-sheet image, not many screenshots.

## Where things live (local drive, never cloud folders)

`/Volumes/AARVO Lab/9-English with Sena/` (request folder access to `/Volumes/AARVO Lab` if not connected)

- `NNN/Clips/` — the episode's clips, end card image, thumbnail. Episodes 1 and 2 are in `1-` and `2-`; later ones are `003`, `004` …
- `NNN/Export/` — finished video goes here, one file only.
- `Brand/` — `Lovetto (CapCut).ttf`, `heart_frames/` (CapCut's animated heart, 49 PNG frames), `Pastel Groove.wav`.
- `_Script/build.py` — the builder. `MD/` — the 100-day phrase plan and production masters.

## Steps

1. **Check the folder.** `Clips` needs four clips and an end card image. Note the playing order (ask if file names don't make it obvious).
2. **Get words and timing from the audio.** Use ffmpeg `silencedetect` (noise -32dB, d 0.25) to find each spoken line, then transcribe each segment with sherpa-onnx Whisper base.en (`pip install sherpa-onnx soundfile`; model from the k2-fsa sherpa-onnx GitHub releases, `sherpa-onnx-whisper-base.en.tar.bz2`). faster-whisper cannot download its model here.
3. **Correct the text** against the episode's pairs in `MD/Sena_Pudding_100_Day_English_Shorts_Plan.md` (the recogniser mishears names: "Cena", "putting").
4. **Write `Clips/episode.json`:** `name`, `end_card`, and per clip a `file` and `lines`, each line with `role`, `start`, `end`, `text`. Roles: `pudding` (simple phrase), `sena` (polished phrase, must directly follow its `pudding` line), `sena_c` / `pudding_c` (centred line for intro, banter and the closing question).
5. **Judge each clip.** If the end of a clip is bad (glitch, frozen frame, stray sound) or a line is unusable, leave it out or trim, and say so in the report.
6. **Build:** `python3 _Script/build.py <episode folder>` from the series folder.
7. **Check:** extract about six frames with ffmpeg into one small contact sheet, look at it once, and confirm music is audible with `volumedetect`.
8. **Report** the phrase pairs as captioned, anything trimmed or guessed, and ask Lillian to play it once, since Claude cannot hear timing.

## The look (fixed in build.py; do not vary per episode)

| | Pudding (simple) | Sena (polished) |
|---|---|---|
| Side | left | right |
| Text | white, black outline | black, white outline |
| Font | Lovetto | Lovetto |
| Size (CapCut units) | 10, or 9 if long | 12, or 11 if long; always bigger |

- Output 1080 × 1920, 30 fps. Both captions centred on the same height (y 1360; CapCut Y -800).
- Equal space to the frame edge on both sides (140 px); nothing may touch or cross the edge.
- At most two words per line; three lines are fine. A single-line caption must be short, otherwise break it.
- Pudding's caption stays up while Sena speaks.
- Heart: CapCut's animated heart at 70% size, centred above Sena's caption (y 1160), appearing with her line. **Only on polished phrases** — never on intro, banter or closing lines.
- Music: Pastel Groove at -6.8 dB under the voices (the level of the approved episode 2), 2-second fade-out. End card 2.7 seconds.
- Episode 2 (made by hand in CapCut, in `2-/Upload`) is the reference for how a finished reel should look and sound.

## Known limits

- Clips are 416 × 752, so footage is soft when upscaled; captions stay sharp.
- Captions appear without CapCut's pop-in animation.
- Deleting on the AARVO Lab drive needs Lillian's permission; move unwanted files to an `Obsolete` folder instead.
- Uploading to YouTube is a separate step and needs her OK each time.