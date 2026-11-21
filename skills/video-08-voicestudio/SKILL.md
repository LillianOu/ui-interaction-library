---
name: video-08-voicestudio
description: Use when a video or audio project needs a voiceover, a translated dub, a transcript or an audiobook made on your own computer without paying per minute. VoiceStudio routes to debpalash's open-source VoiceStudio app, its local API and MCP server.
---
# Video-08 — VoiceStudio

**Category:** 工具庫 / Tool Library · 影片與媒體 / Video & Media
**Powered by:** [debpalash/VoiceStudio](https://github.com/debpalash/VoiceStudio) VoiceStudio (AGPL-3.0)

> This skill is a guide, not a copy. It explains when to use an external tool, how to install it and how to get good results. It contains none of the original's text.

## What it does

VoiceStudio is a free desktop app that does on your own computer what paid voice services do online: text-to-speech, designing a new voice, cloning a voice from a sample, dubbing a video into another language, transcription and audiobook making. It supports hundreds of languages, including Mandarin, and has a local API and MCP server so Claude Code can send it jobs.

## When to use

- Use to dub an English reel into Mandarin (or the reverse) for Chinese-speaking audiences.
- Use for voiceovers on AARVO KIDS stories, ads and product promos (Video-03, Video-04) when you do not want to record yourself.
- Use to make transcripts and captions from a video.
- Do not use to clone anyone's voice without their clear permission.
- Do not use on a low-powered laptop for long jobs; it runs the AI models on your machine.

## Routing

| Job | Use | Why |
| --- | --- | --- |
| Voiceover from a script | VoiceStudio text-to-speech or voice design | No recording needed |
| Translate and dub a video | VoiceStudio dubbing | Transcribes, translates and re-voices |
| Captions for a reel | VoiceStudio transcription, then Video-05 or CapCut | Accurate timed text |
| Build the video itself | Video-01, Video-03, Video-04 | VoiceStudio only makes the audio |

## Install

macOS: `brew tap debpalash/tap && brew install --cask debpalash/tap/voicestudio`, or download the app from the [releases page](https://github.com/debpalash/VoiceStudio/releases/latest). Windows and Linux installers are on the same page.

Requirements: a recent computer. Apple Silicon Macs (macOS 13.3+) or a PC with a good graphics card run it best. Models download on first use and need disk space.

## How to ask

Use the app directly, or with its MCP server connected in Claude Code:

- "Use VoiceStudio to dub this reel into Mandarin with a warm female voice and keep the timing."
- "Use VoiceStudio to read this story script as a gentle children's narrator and export a WAV."

## Watch-outs

- Licence is AGPL-3.0: free to use, but if you change its code and offer it as an online service, you must share your changes.
- Voice cloning: get written permission from the person, and say a voice is AI-made where platforms require it.
- On macOS, a "damaged app" warning is Gatekeeper blocking it, not a broken download; follow the fix in its install guide.

## Credit

VoiceStudio by Palash Debnath (debpalash), AGPL-3.0. Checked on 2026-11-21 at commit `54465ec`.

## Copy-ready English prompt

```text
Use VoiceStudio through its MCP tools. Take <video or script>, <dub it into Mandarin / read it aloud> with <voice description>, keep it in time with the original, and export <WAV / MP4>. Also export a transcript as an SRT file.
```
