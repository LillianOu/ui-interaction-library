---
name: 18-ui-ux-pro-max-uizze
description: Use when a design needs evidence rather than opinion: a matching palette, font pairing or style for a product type, or real shipped screens to ground a layout. UI UX Pro Max + UIZZE routes to nextlevelbuilder's ui-ux-pro-max (local style database) and UIZZE's anti-ui-slop (real-screen references and a finish gate).
---
# 18 — UI UX Pro Max + UIZZE
**Category:** 技能庫 / Skill Library · 設計 / Design
**Powered by:** [nextlevelbuilder/ui-ux-pro-max-skill](https://github.com/nextlevelbuilder/ui-ux-pro-max-skill) `ui-ux-pro-max` (MIT) · [uizze/uizze](https://github.com/uizze/uizze) `anti-ui-slop` (MIT repo; skill marked Apache-2.0)

> This skill is a guide, not a copy. It explains when to call an external skill, how to install it and how to get good results. It contains none of the original skills' text; install the originals to use them.

## What it does

UI UX Pro Max + UIZZE collects references so design choices can be defended. `ui-ux-pro-max` searches a local database of styles, product-specific palettes, font pairings, UX rules and chart types, and can write a design system file for the project. `anti-ui-slop` grounds a screen in UIZZE's catalogue of real web and iOS screens, writes a short design contract and runs a finish check before you call the screen done.

## When to use

- Use when you need a palette, font pairing or style that suits a product type (fintech, kids' education, wellness, B2B dashboard).
- Use when setting up a design system file for a new project.
- Use when a layout should be based on what real, shipped products do for the same screen.
- Do not use to pick an overall aesthetic personality. Call 17 Taste Pack first, then use UI UX Pro Max + UIZZE to fill in the details.

## Routing

| Job | Call | Why |
| --- | --- | --- |
| Palette, fonts, style and UX rules for a product type | `ui-ux-pro-max` | Fast local search; works offline once installed |
| A design system file for a new project | `ui-ux-pro-max` | Generates a master design system with page-level overrides |
| Real screens as references for one screen type | `anti-ui-slop` | Draws on UIZZE's public catalogue of shipped web and iOS screens |
| A pre-ship "is this generic?" check against the product | `anti-ui-slop` | Runs a finish gate that checks states and product fit |

## Install

```bash
npx skills add nextlevelbuilder/ui-ux-pro-max-skill --skill ui-ux-pro-max
npx skills add https://uizze.com --skill anti-ui-slop
```

Requirements: `ui-ux-pro-max` runs its search with Python 3. `anti-ui-slop` needs web access to UIZZE's public catalogue; it works without an account. UIZZE also sells a paid MCP with deeper references, which is optional.

## How to ask

- "Ask UI UX Pro Max + UIZZE for a palette and font pairing for a children's English-learning app."
- "UI UX Pro Max + UIZZE: show me how real apps design a returns-status screen, then draft ours."
- "UI UX Pro Max + UIZZE, run the finish gate on this checkout page."

## Watch-outs

- A database answer is a starting point, not a brand. Adjust it to your own identity.
- `anti-ui-slop` depends on a commercial service's public catalogue; if that changes, the skill's references may shrink.
- Both overlap with 21 Quality Pack on review. Use UI UX Pro Max + UIZZE for references, Quality Pack for the final quality check.

## Credit

`ui-ux-pro-max` by Next Level Builder, MIT, checked at commit `56ea9cf`. `anti-ui-slop` by UIZZE, checked at commit `40b0ee4`. Checked on 2026-10-18.

## Copy-ready English prompt

```text
Use the ui-ux-pro-max skill to propose a design system for <product type> aimed at <audience>: style, primary and accent palette with hex values, a heading and body font pairing, and the top five UX rules for this kind of product. Then use anti-ui-slop to find real screens for <screen type> and explain which patterns we should adopt and which to avoid.
```
