---
name: 17-pearl-peacock-taste-pack
description: Use when choosing the visual direction for a new page or app so it does not look generic or AI-made: distinctive, premium-agency or quiet editorial-minimal. Pearl Peacock routes to Anthropic's frontend-design and Leonxlnx's design-taste-frontend, high-end-visual-design and minimalist-ui.
---
# 17 — 孔雀品味師 / Pearl Peacock (Taste Pack)

**Category:** 設計工具組 / Design Toolkit
**Powered by:** [anthropics/skills](https://github.com/anthropics/skills) `frontend-design` (Apache-2.0) · [Leonxlnx/taste-skill](https://github.com/Leonxlnx/taste-skill) `design-taste-frontend`, `high-end-visual-design`, `minimalist-ui` (MIT)

> A crew member is a guide, not a copy. It explains when to call an external skill, how to install it and how to get good results. It contains none of the original skills' text; install the originals to use them.

## What it does

Pearl Peacock decides how a page should look and feel before it is built. The four skills behind it all fight "AI slop" (purple gradients, identical cards, centred hero with three icons), but each pushes towards a different taste. Pearl Peacock picks one, so they do not pull in different directions at once.

## When to use

- Use when starting a landing page, portfolio, product page or app shell and the look is not decided.
- Use when an existing page "looks like every other AI site" and needs a clear point of view.
- Do not use to check a finished UI for bugs, accessibility or polish. Call 21 Hawk Inspector.
- Do not use to look up palettes, font pairings or real reference screens. Call 18 Magpie Muse.

## Routing

Pick one direction per project. Installing all four is fine; calling more than one on the same page is not.

| Direction | Call | Best for |
| --- | --- | --- |
| Distinctive, brief-specific identity | `frontend-design` | Any brief where the look should come from the subject itself; already built into Claude, so no install needed in Claude apps |
| Researched art direction with a screenshot check loop | `design-taste-frontend` | Marketing sites, portfolios and one-pagers; studies gallery-grade sites and inspects the result in a real browser |
| Expensive, agency-style polish | `high-end-visual-design` | Premium brands, product launches, jewellery and luxury retail |
| Calm editorial minimalism | `minimalist-ui` | Content-led sites, notes-style apps, portfolios that let work speak; warm monochrome, no gradients |

## Install

```bash
# frontend-design is already available in Claude apps; for other agents:
npx skills add anthropics/skills --skill frontend-design
# The three Leonxlnx directions (install only the ones you want):
npx skills add https://github.com/Leonxlnx/taste-skill --skill design-taste-frontend
npx skills add https://github.com/Leonxlnx/taste-skill --skill high-end-visual-design
npx skills add https://github.com/Leonxlnx/taste-skill --skill minimalist-ui
```

Requirements: `design-taste-frontend` runs its browser check with Node 22+ and an installed Chrome, Edge or Chromium, and needs network access to find images. The other three need nothing extra.

## How to ask

- "Ask Pearl Peacock for a premium direction for the AARVO Shop jewellery homepage."
- "Pearl Peacock, minimal: redesign my portfolio case-study page."
- "Pearl Peacock: three directions for this landing page, then I'll pick."

## Watch-outs

- These skills are opinionated and will overrule your brand if you let them. Give them your brand colours, fonts and logo first.
- `high-end-visual-design` leans on heavy motion and layered cards; check performance on a mid-range phone.
- Taste is not usability. Always finish with 21 Hawk Inspector.

## Credit

`frontend-design` by Anthropic, Apache-2.0, checked at commit `dbd4588`. `design-taste-frontend`, `high-end-visual-design` and `minimalist-ui` by Leonxlnx, MIT, checked at commit `f624f37`. Checked on 2026-10-18.

## Copy-ready English prompt

```text
Use the <frontend-design | design-taste-frontend | high-end-visual-design | minimalist-ui> skill to set the visual direction for <page>. Audience: <who>. Brand: <colours, fonts, logo, tone words>. Avoid generic AI patterns. Before building, state the direction in five lines (idea, layout, type, palette, motion), then build it and show a screenshot.
```
