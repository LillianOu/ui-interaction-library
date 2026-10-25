---
name: 31-costume-chameleon-awesome-design-md
description: Use when a build needs a complete, consistent visual system fast and a known product's look is a good starting point — drop one brand-inspired DESIGN.md into the project so every generated screen follows the same colours, type, components and rules. Costume Chameleon routes to VoltAgent's awesome-design-md collection (84 DESIGN.md files) and Google's DESIGN.md linter.
---
# 31 — 變色龍換裝師 / Costume Chameleon (Awesome DESIGN.md)

**Category:** 設計工具組 / Design Toolkit
**Powered by:** [VoltAgent/awesome-design-md](https://github.com/VoltAgent/awesome-design-md) (MIT) · browsable previews at [getdesign.md](https://getdesign.md) · [Google Stitch DESIGN.md format](https://stitch.withgoogle.com/docs/design-md/specification/) and its `@google/design.md` linter

> A crew member is a guide, not a copy. It explains when to call an external resource, how to install it and how to get good results. It contains none of the original files' text; install the originals to use them.

## What it does

`AGENTS.md` tells a coding agent how to build a project; `DESIGN.md` tells it how the project should look. A DESIGN.md is one plain-text file holding a design system: tokens for colour, type, spacing, radius and elevation in its front matter, then written rules for mood, components, layout, responsive behaviour and do's and don'ts. awesome-design-md is a collection of 84 of these, each an analysis of a well-known product's public website. Costume Chameleon helps you pick the right costume, put it on the project, and then change it into your own outfit so the result is consistent but not a clone.

## When to use

- Use when you are vibe coding a prototype, landing page, dashboard or app shell and every screen comes out looking different.
- Use when you know the feel you want ("Linear-precise", "Notion-warm", "Apple-premium") and want that translated into tokens and rules an agent will follow.
- Use when you want to study how a mature product structures its design system before writing your own.
- Use as the first draft of your own brand's DESIGN.md: start from the closest costume, then replace the identity.
- Do not use to decide what the aesthetic should be in the first place. Call 17 Pearl Peacock.
- Do not use to find a palette or font pairing suited to a product category (kids' education, wellness). Call 18 Magpie Muse.
- Do not use to judge a finished screen. Call 21 Hawk Inspector.

## Routing

Pick by the feeling you want, not the company. Folder names (the `<slug>` used in Install) are in code.

| Feeling you want | Try | Why |
| --- | --- | --- |
| Premium, quiet, lots of white space | `apple`, `vercel` | Restrained palettes and strong type hierarchy; good for a portfolio |
| Precise product tool, dark, minimal | `linear.app`, `raycast`, `superhuman` | Dense, keyboard-first app shells with one accent colour |
| Warm, editorial, soft | `notion`, `claude`, `oura` | Serif or warm-neutral reading surfaces for content and education products |
| Friendly and playful but credible | `figma`, `lovable`, `zapier`, `wise` | Bright accents and rounded shapes without looking childish |
| Fintech trust and polish | `stripe`, `mercury`, `revolut` | Careful numeric type, calm surfaces, strong primary actions |
| Image-led shopping or marketplace | `airbnb`, `pinterest`, `nike`, `shopify` | Photography-first grids and clear buy paths; useful for e-commerce |
| Motion-forward marketing site | `framer`, `webflow`, `clay` | Expressive layouts that pair well with this library's motion skills |
| Retro or Y2K mood | `nintendo-2001`, `dell-1996` | From the collection's nostalgia series; good for one-off campaign pages |
| Write or check a DESIGN.md yourself | `npx @google/design.md lint` | Flags broken token references, low contrast and unused tokens |

The full list is in the collection's README, grouped by industry. Preview a costume's swatches, type scale and components on getdesign.md before installing it.

## Install

A costume is one file, not a skill. Put it in the root of the project you are building:

```bash
# replace <slug> with a folder name from the table above, e.g. linear.app
curl -L -o DESIGN.md \
  https://raw.githubusercontent.com/VoltAgent/awesome-design-md/main/design-md/<slug>/DESIGN.md
```

Or clone the whole collection once and copy from it:

```bash
git clone --depth 1 https://github.com/VoltAgent/awesome-design-md ~/design-md-costumes
cp ~/design-md-costumes/design-md/notion/DESIGN.md ./DESIGN.md
```

Check it after any edit:

```bash
npx @google/design.md lint DESIGN.md
```

Requirements: network access to GitHub; Node.js for the linter. Claude Code, Cursor, Codex and Google Stitch all read a DESIGN.md in the project root; in other tools, attach the file or tell the agent to read it first.

## How to ask

- "Costume Chameleon: suggest three DESIGN.md costumes for a premium, minimal designer portfolio, with one line on why each fits."
- "Ask Costume Chameleon to put the notion costume on this project, then build the pricing page following DESIGN.md."
- "Costume Chameleon, turn this costume into our own brand: swap in our colours and fonts, rename it, and lint it."

## Watch-outs

- These are other companies' identities. Use them to prototype and learn. For anything public or sold, change the costume first: your own primary colour, your own typefaces, your own name in the front matter. A shipped page that reads as "Stripe with a new logo" damages your credibility and can raise trademark issues.
- Many costumes name proprietary fonts (Söhne, SF Pro, SoDoSans and similar). You need a licence to use them. Replace them with open fonts of a similar character, and update the file so the agent stops reaching for them.
- The files are analyses of public CSS, not official design systems. Values can be wrong or out of date; trust your eye and the linter over the file.
- Some costumes describe a marketing site, not an app. If you are building a dashboard, check that the file covers forms, tables and states, or fill the gaps yourself.
- A DESIGN.md sets the look, not the interaction. Pair it with this library's interaction skills (01–13, 22–30) for motion and behaviour, and check contrast and focus states with 21 Hawk Inspector — a borrowed palette does not guarantee accessibility in your layout.
- Keep exactly one DESIGN.md per project. Two competing systems produce the inconsistency you were trying to fix.

## Credit

Collection by VoltAgent and contributors, MIT. DESIGN.md format by Google Stitch. Checked on 2026-10-25 at commit `3b60532` (84 DESIGN.md files).

## Copy-ready English prompt

```text
Read DESIGN.md in the project root before writing any UI and treat it as the source of truth for colour, typography, spacing, radius, elevation and component styles. Build <page or screen> for <product and audience>. Use only tokens defined in DESIGN.md; if you need a value it does not define, add it to DESIGN.md first and tell me. Follow its do's and don'ts. Replace any proprietary font it names with <open font>. When finished, list any place where you had to depart from DESIGN.md and why.
```
