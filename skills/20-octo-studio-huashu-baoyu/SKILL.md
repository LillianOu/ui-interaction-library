---
name: 20-octo-studio-huashu-baoyu
description: Use when one prompt should produce a finished design deliverable as HTML: high-fidelity prototype, slide deck, animation, infographic or mockup, kept in your own files. Octo Studio routes to alchaincyf's huashu-design, JimLiu's baoyu-design and, for a full local design workspace, nexu-io's Open Design.
---
# 20 — 章魚工作室 / Octo Studio (Huashu + Baoyu)

**Category:** 設計工具組 / Design Toolkit
**Powered by:** [alchaincyf/huashu-design](https://github.com/alchaincyf/huashu-design) (MIT) · [JimLiu/baoyu-design](https://github.com/JimLiu/baoyu-design) (MIT) · [nexu-io/open-design](https://github.com/nexu-io/open-design) (Apache-2.0, app + MCP server)

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
| A whole design workspace: projects, design systems, previews and team review in one app | Open Design | A local desktop or web app that drives the coding agent you already have (Claude Code, Codex and others) or your own API key. Every output follows a chosen design system or your DESIGN.md, opens in a sandboxed preview, and can be shared for feedback. Its MCP server lets agents in other repos read the live tokens and components. |

## Install

```bash
npx skills add alchaincyf/huashu-design
npx skills add JimLiu/baoyu-design
```

Open Design is an app, not a skill. Download the macOS or Windows desktop app from open-design.ai (no Node needed), then connect it to your agent:

```bash
od mcp install claude          # or codex, cursor, copilot
```

On Linux there is no desktop build; run it from source (Node 24 and pnpm) or with Docker, as its README describes.

Requirements: Node to run the installer. `huashu-design` uses Python 3 and Playwright for checks and exports. `baoyu-design` is happiest with Python 3 for its local preview server.

## How to ask

- "Ask Octo Studio for a 10-slide AARVO.AI workshop deck, exported as PowerPoint."
- "Octo Studio, three directions: a launch infographic for the LINE sticker set."
- "Octo Studio: high-fidelity prototype of the portfolio home page."
- "Octo Studio, Open Design: start a project for the returns app using our DESIGN.md, and make the dashboard and mobile scan screens."

## Watch-outs

- Open Design is a large, fast-moving product (dozens of releases, hundreds of bundled skills). It is the right choice when you want one place for many deliverables; for a single deck or prototype, a skill is lighter. Some reliability telemetry is always on; check its privacy settings before using it with client work.
- A community "Claude Design Skill" (jiji262/claude-design-skill) is often listed alongside these. Its own README says it is a restructured copy of the system prompt of Anthropic's hosted Claude Design product, whose content belongs to Anthropic, so it does not meet this crew's open-licence rule and is not wrapped here. Claude apps already include Claude Design itself; use that.
- huashu-design and baoyu-design overlap heavily. Install both, but call one by name per job, or they will both try to answer "make a deck".
- For flip-style video reels, Flip Fox (HyperFrames) in Lillian's crew repo is the tested route; use Octo Studio for decks and prototypes.
- These are presentation artefacts. Rebuild anything that ships to real users with 19 Builder Ant and check it with 21 Hawk Inspector.

## Credit

`huashu-design` by alchaincyf (花叔), MIT, checked at commit `798c423`. `baoyu-design` by Jim Liu (宝玉), MIT, checked at commit `6530033`. Checked on 2026-10-18. Open Design by nexu-io, Apache-2.0, checked on 2026-10-29 at commit `06de116` (v0.25.1).

## Copy-ready English prompt

```text
Use the <huashu-design | baoyu-design> skill to create a <prototype | slide deck | infographic | animation> for <project>. Audience: <who>. Content: <key points or screens>. Brand: <colours, fonts, logo>. Output self-contained HTML in ./design/<name>/, and <export to PPTX | export MP4> when done.
```
