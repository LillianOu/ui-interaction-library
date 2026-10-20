---
name: 17-pearl-peacock-taste-pack
description: Use when a website, landing page, portfolio or app screen (web dashboard or mobile app) needs a visual direction that does not look generic or AI-made, when an existing UI needs a restyle, or when you want a reference board before code. Pearl Peacock routes to Leonxlnx's Taste Skill family (design-taste-frontend, the classic dial-based variants and the image-generation reference skills) and Anthropic's frontend-design.
---
# 17 — 孔雀品味師 / Pearl Peacock (Taste Pack)

**Category:** 設計工具組 / Design Toolkit
**Powered by:** [Leonxlnx/taste-skill](https://github.com/Leonxlnx/taste-skill) `design-taste-frontend` (MIT) · [Leonxlnx/taste-skill-classics](https://github.com/Leonxlnx/taste-skill-classics) `high-end-visual-design`, `minimalist-ui`, `industrial-brutalist-ui`, `gpt-taste`, `design-taste-frontend-v2-experimental` (MIT) · [Leonxlnx/imagegen-skills](https://github.com/Leonxlnx/imagegen-skills) `imagegen-frontend-web`, `imagegen-frontend-mobile`, `brandkit`, `image-to-code` (MIT) · [anthropics/skills](https://github.com/anthropics/skills) `frontend-design` (Apache-2.0)

> A crew member is a guide, not a copy. It explains when to call an external skill, how to install it and how to get good results. It contains none of the original skills' text; install the originals to use them.

## What it does

Pearl Peacock decides how a page or screen should look before anything is built, and keeps one taste in charge of the whole project. AI tools left alone produce the average of everything they have seen: flat hierarchy, random spacing, a blue-purple gradient and a row of identical icon cards. Taste Skill replaces those defaults with written, checkable design decisions. Pearl Peacock tells you which of its many variants to call for the job in front of you.

## When to use

- Use when starting a landing page, portfolio, product site or app shell and the look is not decided.
- Use when designing app screens: web dashboards, settings, inboxes, or mobile app flows.
- Use when an existing page or screen "looks like every other AI site" and needs a restyle without a rebuild.
- Use when you want to see the direction as a reference board (web, mobile or brand kit) before any code is written.
- Do not use to check a finished UI for bugs, accessibility or polish. Call 21 Hawk Inspector.
- Do not use to look up palettes, font pairings or real reference screens from existing products. Call 18 Magpie Muse.

## Routing

Pick one direction per project. Installing several is fine; running more than one on the same page is not.

### Build in code

| Job | Call | Notes |
| --- | --- | --- |
| Default for any website or web app screen | `design-taste-frontend` | Current Taste Skill (v2.1). A script offers three researched directions, you pick one, then it builds and checks the result in a real browser at three widths. Has a separate route for app screens (dashboards, admin, settings, inboxes). |
| Restyle an existing page or screen | `design-taste-frontend` | Ask for a redesign. It records the "before", keeps your stack and content, then changes type, colour, layout, states and stock components in order, and shows before and after. (The old `redesign-existing-projects` skill was folded into this.) |
| Brief-specific look, no setup | `frontend-design` | Built into Claude apps. Good when Node and a browser are not available. |
| Tune the look with three dials | `design-taste-frontend-v2-experimental` | The version shown in most social posts. You set three 1–10 numbers at the top: layout variance (symmetric → asymmetric), motion intensity (hover only → scroll and magnetic effects), visual density (airy → packed data). |
| Expensive, agency-style polish | `high-end-visual-design` | Premium brands, launches, jewellery and luxury retail. |
| Calm editorial minimalism | `minimalist-ui` | Content-led sites, notes-style apps, portfolios that let work speak. |
| Hard Swiss / brutalist | `industrial-brutalist-ui` | Bold type, sharp contrast, experimental grids. |
| Stricter rules for GPT or Codex | `gpt-taste` | Use when the coding agent is not Claude. |

The classic skills (everything in `taste-skill-classics`) only run when you call them by name. They will not trigger on their own.

### Reference board first, code second

| Job | Call | Notes |
| --- | --- | --- |
| Website comps: hero, landing, long page | `imagegen-frontend-web` | Produces images only. Use with an image model (ChatGPT Images, Firefly, Gemini), then hand the frames to the coding agent. |
| Mobile app screens and flows | `imagegen-frontend-mobile` | iOS, Android or cross-platform; keeps a set of screens consistent. Also uses the three dials. |
| Brand kit board: logo directions, palette, type, applications | `brandkit` | Lock the brand before pages are made, so every page follows it. |
| One workflow: generate references, analyse, then code | `image-to-code` | Say "generate images, then analyse, then code" in the prompt. |

## Install

```bash
# Default (start here):
npx skills add https://github.com/Leonxlnx/taste-skill --skill design-taste-frontend

# Classic variants, only the ones you want:
npx skills add https://github.com/Leonxlnx/taste-skill-classics --skill design-taste-frontend-v2-experimental
npx skills add https://github.com/Leonxlnx/taste-skill-classics --skill high-end-visual-design
npx skills add https://github.com/Leonxlnx/taste-skill-classics --skill minimalist-ui

# Reference boards:
npx skills add https://github.com/Leonxlnx/imagegen-skills --skill imagegen-frontend-web
npx skills add https://github.com/Leonxlnx/imagegen-skills --skill imagegen-frontend-mobile
npx skills add https://github.com/Leonxlnx/imagegen-skills --skill brandkit

# frontend-design is already available in Claude apps; for other agents:
npx skills add anthropics/skills --skill frontend-design
```

Requirements: `design-taste-frontend` runs its scripts with Node 22+ and an installed Chrome, Edge or Chromium, and needs network access to find pictures; no API keys. The classic and image-generation skills need nothing extra; the image skills need an image model to render.

## How to ask

- "Pearl Peacock: give me three directions for the AARVO Shop jewellery homepage, then I'll pick."
- "Pearl Peacock, restyle: this portfolio case-study page looks generic. Keep the content."
- "Pearl Peacock, app screen: design the dashboard for my 3PL returns app."
- "Pearl Peacock, mobile board: six screens for a kids' learning app, then build screen one."
- "Pearl Peacock, dials: variance 7, motion 3, density 2, for a minimal portfolio hero."

## Watch-outs

- Taste Skill changed on 2026-10-19 (v2.1.3): one skill stays in the main repo; the classics and image skills moved to two new repos with the same install names. Posts made before then show old install paths. Ignore any `uv add taste-skill` command; the real installer is `npx skills add`.
- The three dials belong to the classic and image-generation skills. The current default does not use them; it offers researched directions instead.
- These skills are opinionated and will overrule your brand if you let them. Give them your brand colours, fonts and logo first, or run `brandkit` first.
- Good taste still needs a good brief, the right references and your judgement. The skill does not make every output a masterpiece.
- `high-end-visual-design` leans on heavy motion and layered cards; check performance on a mid-range phone.
- Taste is not usability. Always finish with 21 Hawk Inspector.

## Credit

`design-taste-frontend` by Leonxlnx, MIT, checked at commit `63aba5f`. Classic skills by Leonxlnx, MIT, checked at `taste-skill-classics` commit `5e08c93`. Image-generation skills by Leonxlnx, MIT, checked at `imagegen-skills` commit `beb16b0`. `frontend-design` by Anthropic, Apache-2.0, checked at commit `dbd4588` on 2026-10-18. Taste Skill repos checked on 2026-10-20.

## Copy-ready English prompt

```text
Use the <design-taste-frontend | design-taste-frontend-v2-experimental | high-end-visual-design | minimalist-ui | imagegen-frontend-web | imagegen-frontend-mobile | brandkit> skill for <page or screen>.
Type of work: <new page | restyle of an existing page | app screen | mobile flow | reference board>.
Audience: <who>. Goal: <what the user should do>.
Brand: <colours, fonts, logo, three tone words>.
Dials (classic and image skills only): variance <1-10>, motion <1-10>, density <1-10>.
Before building, state the direction in five lines (idea, layout, type, palette, motion). Then build it, show screenshots at phone and desktop width, and list anything that still looks templated.
```
