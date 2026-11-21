---
name: video-07-remotion-skills
description: Use when an AI should build, preview or render any video in Remotion (React code to MP4) from scratch, such as title cards, explainers, captioned clips, map animations or a video app, and write correct Remotion code first time. Routes to Remotion's official agent skills.
---
# Video-07 — Remotion Skills (official)

**Category:** 工具庫 / Tool Library · 影片與媒體 / Video & Media
**Powered by:** [remotion-dev/skills](https://github.com/remotion-dev/skills) (official, by Remotion)
**Licence:** the skills repo has no licence file. Remotion itself uses the [Remotion License](https://www.remotion.dev/docs/license): free for individuals and very small companies, a paid company licence above that. Added at Lilian's request on 2026-11-21 as a link-only guide; nothing from the skills is copied here.
**Docs:** https://www.remotion.dev/docs/ai/skills

> This skill is a guide, not a copy. It explains when to call an external skill, how to install it and how to get good results. It contains none of the original skills' text; install the originals to use them.

## What it does

Remotion makes videos from React code: each frame is a web page, rendered into an MP4. The official skills teach an AI agent how Remotion actually works, so it writes code that runs instead of guessing at the API. The set covers starting a project, writing the video itself (layout, animation, type, media, audio, timing), previewing in Remotion Studio, rendering, captions, map animations, building a video product, looking up the docs, upgrading and licence questions. One umbrella skill points to the rest when you are not sure which to call.

## When to use

- Use to build a custom video in Remotion from scratch: title cards, animated explainers, data stories, captioned clips, map routes.
- Use to fix or extend a Remotion project, including Video-04 Remotion Shotcraft and Video-06 story-to-handdrawn-video renders, when the AI gets Remotion code wrong.
- Use when you want to turn a video template into a product (for example personalised videos made from data).
- Do not use for website or app promo videos. Use Video-04 Remotion Shotcraft, which has the shot recipes ready.
- Do not use for reels built from HTML. Use Video-01 HyperFrames Video or Video-02 HyperFrames Pack. Pick one video tool per session.
- Do not use to choose which motion to make. Use Design-15 Motion Prompt first.

## Routing

| Job | Call | Why |
| --- | --- | --- |
| Not sure which | `remotion-best-practices` | Umbrella skill that points to the right one |
| New project or composition | `remotion-create` | Sets up the project and first video |
| Write the video | `remotion-markup` | Layout, animation, type, media, audio and timing rules |
| See it | `remotion-studio` | Opens the live preview |
| Export | `remotion-render` | Renders a video or a still |
| Subtitles | `remotion-captions` | Captions and subtitles |
| Map animation | `remotion-maps` | Routes, markers and flyovers |
| Video product | `remotion-saas` | Architecture for a Remotion-powered app |
| Check the API | `remotion-docs` | Searches current Remotion docs |
| Licence questions | `remotion-license` | Where the licence, FAQ and pricing live |
| Update | `remotion-upgrade` | Upgrades Remotion and these skills |

## Install

**In a Remotion project:**

```bash
npx remotion skills add
```

**Anywhere else (Claude Code, Codex, Cursor and other agents):**

```bash
npx skills add remotion-dev/skills
```

New projects can include them from the start with `npx create-video@latest --skills`.

**Claude app (no Terminal):** download the repo as a ZIP, zip the one skill folder you want from `skills/` (start with `remotion-best-practices`), upload it in Settings → Skills and switch it on.

Requirements: Node.js and a Remotion project; rendering uses a headless Chrome. In the cloud workspace, use the headless-shell browser and 2-core concurrency tips from Video-04 Remotion Shotcraft.

## How to ask

- "Use the Remotion skills to make a 10-second 9:16 title card for AARVO.AI with my brand colours, preview it in Studio, then render."
- "Use remotion-captions to add word-by-word captions to this clip."
- "Use remotion-maps to animate a route from Sydney to Taipei."

## Watch-outs

- **Licence:** check the Remotion License before using it for client or company work; companies above the free size need a paid licence. Ask `remotion-license` if unsure.
- Overlaps with Video-04 Remotion Shotcraft and Video-06 story-to-handdrawn-video, which both render with Remotion. Use those for their own jobs and this set for custom builds or fixing Remotion code.
- Render a still or a short draft before a full render; full renders are slow.
- The skills update with each Remotion release. Run `remotion-upgrade` now and then.

## Credit

Remotion Agent Skills by Remotion (remotion-dev). Checked on 2026-11-21 at commit `3e20ac7` (skills version 4.0.544).

## Copy-ready English prompt

```text
Use the Remotion skills (start with remotion-best-practices). Make a <length>-second <aspect ratio> video about <subject> using my brand colours and fonts. Show me a still of the key frame first, then render a draft.
```
