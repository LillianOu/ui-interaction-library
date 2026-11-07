---
name: design-14-unslop
description: Use when a vibecoded screen (dashboard, app or landing page) looks AI-generated — purple gradients, glows, emoji labels, "New ✨" badges, uneven spacing — and should be redesigned into something with its own character while keeping its features and content. Routes to heydamir's unslop skill.
---
# Design-14 — unslop
**Category:** 工具庫 / Tool Library · 設計 / Design
**Powered by:** [heydamir/unslop](https://github.com/heydamir/unslop) `unslop` by Damir Sokolovsky (CC BY 4.0: free to use, change and share, including commercially, as long as the author is credited and the repo is linked)

> This skill is a guide, not a copy. It explains when to call an external skill, how to install it and how to get good results. It contains none of the original skill's text; install the original to use it.

## What it does

unslop takes a screen that obviously came out of an AI builder and redesigns it so it looks like a designer made it for this one product. It first audits the screen against a list of common "AI look" tells and judges how bad it is: heavy, light or none. It then writes a short visual direction from the product itself (what it does, its character, the world it belongs to, one or two rich moments, one signature detail) and stops to let you approve it. After that it fixes the screen in a fixed order of passes: spacing, colour, icons, copy, type, layout, details, visuals and motion. Features, content and section order stay; every size, colour and word becomes deliberate. It can also generate a hero image when an image tool is available, save a live website as an editable copy, and record a before-and-after "story" video of the redesign.

## When to use

- Use when a screen you built with Lovable, Bolt, v0, Claude or Cursor works but looks generic or "AI-made".
- Use on dashboards (including Etsy dashboard designs), app screens and landing pages in React, Tailwind, HTML or CSS.
- Use when you only have a screenshot or a live link: it can rebuild the screen as HTML first, then redesign that.
- Use when you want a before-and-after video of a redesign to post.
- Do not use to choose a look for a page that does not exist yet. Call Design-03 Taste Pack for direction, then build.
- Do not use for a final accessibility, bug and polish check. Call Design-13 Quality Pack after unslop.
- Do not use for removing AI tells from writing. It works on interfaces only.

## Routing

| Job | Call | Why |
| --- | --- | --- |
| Redesign an existing screen that looks AI-made | `unslop` | Audit, direction, then nine ordered passes |
| Screen is mostly fine, a few tells left | `unslop` (it switches to polish mode) | Fixes only what the audit found, keeps the brand |
| Live website, no code | `unslop` + its `scripts/snapshot.mjs` | Saves the page as HTML to redesign |
| Before-and-after video for social | `unslop` + its `scripts/story.mjs` | Renders the redesign pass by pass to video |

## Install

Claude.ai or Claude desktop (no Terminal): download the repo as a ZIP from [heydamir/unslop](https://github.com/heydamir/unslop) (green Code button → Download ZIP), zip only the `skills/unslop` folder, then upload it in Settings → Skills and switch it on. Code execution must be on.

Claude Code:

```bash
git clone https://github.com/heydamir/unslop
mkdir -p ~/.claude/skills && cp -r unslop/skills/unslop ~/.claude/skills/
```

Codex: `$skill-installer install https://github.com/heydamir/unslop/tree/main/skills/unslop`

Requirements: none for the audit and redesign. Saving a live site and the story video need Node with Playwright and Chromium (`npm install -D playwright && npx playwright install chromium`); the video also needs ffmpeg.

## How to ask

- "/unslop this dashboard" (attach the file or paste the code).
- "Unslop the hero of https://example.com and give me the redesigned HTML."
- "Unslop my Etsy dashboard design. Polish mode only, keep my colours."
- "Unslop my landing page and make the story video so I can post it."

## Watch-outs

- It stops after the audit and direction and waits for your yes. Read the five direction lines carefully; changing direction later means redoing every pass.
- It changes copy: no exclamation marks, no hype words, unverifiable claims like "10,000+ users" are flagged or removed. Check it did not drop wording you need.
- From a link or screenshot it produces a redesigned page in code, not a change to the real site. Someone still has to move it into the real project.
- Design opinions are strong and subjective (for example, no bold headings, no uppercase labels). Overrule it where your brand needs otherwise.
- Saving a live page loads that site's content; only use it on pages you own or are allowed to copy.
- Generated hero images may use a paid image service.
- Licence is CC BY 4.0. If you share or sell anything adapted from the skill itself, credit Damir Sokolovsky and link the repo. Designs you make with it are yours.
