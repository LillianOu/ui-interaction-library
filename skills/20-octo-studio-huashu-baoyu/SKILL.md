---
name: 20-octo-studio-huashu-baoyu
description: Use when one prompt should produce a finished design deliverable as HTML: high-fidelity prototype, slide deck, animation, infographic or mockup, kept in your own files. Octo Studio routes to alchaincyf's huashu-design and JimLiu's baoyu-design.
---
# 20 — 章魚工作室 / Octo Studio (Huashu + Baoyu)

**Category:** 設計工具組 / Design Toolkit
**Powered by:** [alchaincyf/huashu-design](https://github.com/alchaincyf/huashu-design) (MIT) · [JimLiu/baoyu-design](https://github.com/JimLiu/baoyu-design) (MIT)

> A crew member is a guide, not a copy. It explains when to call an external skill, how to install it and how to get good results. It contains none of the original skills' text; install the originals to use them.

## What it does

Octo Studio is the crew's many-armed production desk. Both skills behind it turn a brief into a polished, self-contained HTML deliverable that stays in your own project folder. `huashu-design` always shows three directions first, then builds the chosen one, and can export decks and animations (including MP4 and GIF). `baoyu-design` brings a Claude Design-style workflow into your local editor and covers prototypes, app screens, dashboards, decks with PowerPoint export, résumés, HTML email and more.

## When to use

- Use when you want a finished-looking prototype, pitch deck, infographic or short animation from one request.
- Use when the files must live in your own repo or folder rather than in a hosted tool.
- Use when presenting a concept to a client and you want options to choose from (huashu-design).
- Do not use for production web apps with a backend. Both skills say so; use 19 Builder Ant.
- Do not use for a rough flow check. Call 15 Sketch Squirrel first.

## Routing

| Job | Call | Why |
| --- | --- | --- |
| Three directions to choose from, then a high-fidelity build | `huashu-design` | Its three-direction step is mandatory, even with a set brand |
| Animated piece or video export (MP4, GIF) | `huashu-design` | Includes animation and export tooling |
| Chinese-language deck or prototype | `huashu-design` | Written in Chinese with Chinese trigger words |
| Prototype, app screens or dashboard in a local Claude Design-style flow | `baoyu-design` | Built as a local equivalent of Claude Design |
| Deck that must become a PowerPoint file | `baoyu-design` | Exports its own decks to PPTX |
| Résumé, HTML email or document layout | `baoyu-design` | Covers these formats directly |

## Install

```bash
npx skills add alchaincyf/huashu-design
npx skills add JimLiu/baoyu-design
```

Requirements: Node to run the installer. `huashu-design` uses Python 3 and Playwright for checks and exports. `baoyu-design` is happiest with Python 3 for its local preview server.

## How to ask

- "Ask Octo Studio for a 10-slide AARVO.AI workshop deck, exported as PowerPoint."
- "Octo Studio, three directions: a launch infographic for the LINE sticker set."
- "Octo Studio: high-fidelity prototype of the portfolio home page."

## Watch-outs

- The two overlap heavily. Install both, but call one by name per job, or they will both try to answer "make a deck".
- For flip-style video reels, Flip Fox (HyperFrames) in Lillian's crew repo is the tested route; use Octo Studio for decks and prototypes.
- These are presentation artefacts. Rebuild anything that ships to real users with 19 Builder Ant and check it with 21 Hawk Inspector.

## Credit

`huashu-design` by alchaincyf (花叔), MIT, checked at commit `798c423`. `baoyu-design` by Jim Liu (宝玉), MIT, checked at commit `6530033`. Checked on 2026-10-18.

## Copy-ready English prompt

```text
Use the <huashu-design | baoyu-design> skill to create a <prototype | slide deck | infographic | animation> for <project>. Audience: <who>. Content: <key points or screens>. Brand: <colours, fonts, logo>. Output self-contained HTML in ./design/<name>/, and <export to PPTX | export MP4> when done.
```
