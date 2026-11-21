---
name: design-18-astryx
description: Use when building a React app, dashboard or product UI and you want a complete, themeable, accessible component set that AI agents can read and build with correctly. Astryx routes to Meta's open-source Astryx design system, its CLI and its agent docs.
---
# Design-18 — Astryx

**Category:** 工具庫 / Tool Library · 設計 / Design
**Powered by:** [facebook/astryx](https://github.com/facebook/astryx) Astryx (MIT)

> This skill is a guide, not a copy. It explains when to use an external tool, how to install it and how to get good results. It contains none of the original's text.

## What it does

Astryx is Meta's design system, used inside the company for years and now open source. It gives you 150+ accessible React components (buttons, inputs, tables, navigation, app shells), themes with dark mode, and ready-made page templates. It is built for AI agents too: a CLI and docs let Claude look up the real components and props instead of inventing them, so generated UI matches the system.

## When to use

- Use when building a dashboard, admin screen or app (for example Returns Bench or an Etsy dashboard template) and you want consistent, accessible parts instead of starting from scratch.
- Use when you want one theme (colours, type, radius) applied across a whole product.
- Use the templates as a starting point, then add effects from the UI Library.
- Do not use for a one-page portfolio or landing page with a custom look; plain HTML/CSS and the UI Library are lighter.
- Do not use outside React.

## Routing

| Job | Use | Why |
| --- | --- | --- |
| Start a new app with the system | `npx @astryxdesign/cli init` | Sets up components and a theme |
| Let the agent look up components | `astryx docs` / the Astryx CLI | Agent uses real props, not guesses |
| Pick layout and navigation patterns | UI-23 Dashboard Nav Patterns, then Astryx components | Pattern first, parts second |
| Plan the dashboard's charts | the dataviz skill | Astryx does not choose chart types |

## Install

In a React project, in Claude Code:

```bash
npm install @astryxdesign/core @astryxdesign/theme-neutral @stylexjs/stylex
npm install -D @astryxdesign/cli
npx @astryxdesign/cli init
```

Requirements: React 19 or newer. No build plugin needed.

## How to ask

- "Use Astryx to build a returns dashboard: app shell, sidebar, a data table with filters and a summary row."
- "Set up an Astryx theme in my brand colours with dark mode."
- "Check the Astryx docs for the right component before building each part."

## Watch-outs

- It is in beta; component names and props can still change between versions.
- Its default look is clean and neutral. Set your own theme so your products do not all look like Meta tools.
- If you sell dashboard templates built on it, keep the MIT licence notice with the code.

## Credit

Astryx by Meta, MIT. Checked on 2026-11-21 at commit `7869990`.

## Copy-ready English prompt

```text
Use the Astryx design system in this React project. Before building each part, look up the real component and props with the Astryx CLI docs. Build <screen> with <layout>, apply a theme using <brand colours>, support dark mode, and list the Astryx components you used.
```
