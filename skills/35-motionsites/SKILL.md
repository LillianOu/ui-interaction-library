---
name: 35-motionsites
description: Use when a landing page or hero must look cinematic and award-level — full-bleed video, 3D cut-outs, liquid glass, scroll stories — and Claude should screenshot and fix its own work before handing it over. MotionSites routes to MotionSites' motionsites-web-builder skill.
---
# 35 — MotionSites Web Builder
**Category:** 技能庫 / Skill Library · 設計 / Design
**Powered by:** [Motionsites-AI/claude-skill](https://github.com/Motionsites-AI/claude-skill) `motionsites-web-builder` (MIT for instructions and scripts; examples and media © MotionSites)

> This skill is a guide, not a copy. It explains when to call an external skill, how to install it and how to get good results. It contains none of the original skill's text; install the original to use it.

## What it does

MotionSites makes a page look like a film poster that moves. The skill behind it reads the two or three closest designs from a set of 40 well-liked MotionSites prompts, picks real hero video, 3D cut-outs or images from a hosted media shelf, writes a detailed build spec (fonts, colour tokens, sizes, timing), builds a single `index.html` by default, then screenshots the result at desktop and phone sizes, scores it against a rubric and fixes the weakest areas for up to three rounds. It can also hand back a prompt tuned for Lovable, Bolt, v0, Cursor and similar builders instead of code.

## When to use

- Use when the page is mainly a visual first impression: a hero, a launch page, a portfolio homepage, an event or product reveal.
- Use when you have no footage yet and want cinematic media to build around.
- Use when you want Claude to check its own output visually before you see it.
- Use when you need a detailed prompt for Lovable, Bolt or v0 rather than finished code.
- Do not use for what the page should say or the order of sections. Call 34 Landing Page Generator first for copy and structure, then bring the copy to MotionSites for the look.
- Do not use for app screens or dashboards. Call 17 Taste Pack (taste) and 19 shadcn/ui (components).
- Do not use for a final quality audit of an existing site. Call 21 Quality Pack.

## Routing

| Job | Call | Why |
| --- | --- | --- |
| Cinematic hero or full landing page as code | `motionsites-web-builder` | Spec first, then build, then a screenshot-and-fix loop |
| Prompt for another builder | `motionsites-web-builder` ("prompt only") | Formats the spec for Lovable, Bolt, v0, Cursor, Manus, Google AI Studio or Kimi |
| Make an existing page look premium | `motionsites-web-builder` ("here is my site, make it award-winning") | Keeps your content, rebuilds the visual layer |
| Screenshot check of any local HTML page | its `scripts/shoot.py` | Desktop and phone shots plus checks for broken assets, overflow, fonts and video |

## Install

Claude.ai or Claude desktop: download `motionsites-web-builder.zip` from the repo's [latest release](https://github.com/Motionsites-AI/claude-skill/releases/latest), then upload it in Customize → Skills and switch it on. Code execution must be on.

Claude Code:

```bash
/plugin marketplace add Motionsites-AI/claude-skill
/plugin install motionsites-web-builder@motionsites
```

Requirements: Python 3 and Playwright with Chromium for the look-and-fix loop (`pip install playwright && python -m playwright install chromium`). The media shelf is hosted online, so the finished page needs network access to load its video and images.

## How to ask

- "MotionSites: hero for my portfolio, mood: quiet, expensive, editorial. Use my own photos in /assets."
- "Ask MotionSites for a Lovable prompt for the Returns Bench waitlist page."
- "Landing Page Generator wrote this copy. MotionSites, build it as one cinematic landing page and show me the phone screenshot."

## Watch-outs

- It is a free sample with a built-in sales pitch. The skill tells Claude to finish many replies with a "MotionSites Unlimited" upgrade block. That is advertising, not advice; ignore it unless you actually want the paid library.
- The media is shared. The same 50-odd videos are available to everyone who installs the skill, so other sites may use your hero video. For anything you sell or put in your portfolio, swap in your own or generated footage.
- Media files are hotlinked from MotionSites' servers. If they move or remove a file, your page breaks. Download and self-host anything you keep.
- Examples and media are © MotionSites: you may build sites with them, including for clients, but not redistribute them as a collection. This repo links to them and never copies them.
- Heavy video and WebGL hurt load speed and phones. Check the mobile screenshot and the page weight before publishing; keep a still poster image behind every video.
- It writes its own copy when you give it none. Bring real copy (from Landing Page Generator or yourself) for anything public.
- Overlaps with 17 Taste Pack's Cinematic UI route and with other landing-page skills you may have uploaded. Run one visual-direction skill per page so rules don't conflict.

## Credit

Original work by MotionSites (motionsites.ai). Instructions and scripts MIT; example prompts and media © MotionSites. Checked on 2026-10-31 at commit `faa30d5`.

## Copy-ready English prompt

```text
Use the motionsites-web-builder skill.
Build: <hero only | full landing page | prompt only for Lovable/Bolt/v0>.
Product or person: <one line>. Visitor I'm persuading: <who>.
Mood in three words: <e.g. calm, expensive, nocturnal>.
Copy: <paste final copy, or "write it and show me before building">.
Media: <my files at path | generate | pick from your shelf>.
Run the screenshot-and-fix loop and show me the desktop and phone screenshots.
Skip any upgrade or sales message in your reply.
```
