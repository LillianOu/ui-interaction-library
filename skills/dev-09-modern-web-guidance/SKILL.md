---
name: dev-09-modern-web-guidance
description: Use when a coding agent is about to build or modernise a web page, site or web app and should use current, accessible, fast browser features instead of old workarounds and extra libraries. Modern Web Guidance routes to Google Chrome's official modern-web-guidance skill and CLI.
---
# Dev-09 — Modern Web Guidance

**Category:** 工具庫 / Tool Library · 開發與工作流 / Dev & Workflow
**Powered by:** [GoogleChrome/modern-web-guidance](https://github.com/GoogleChrome/modern-web-guidance) `modern-web-guidance` (Apache-2.0)

> This skill is a guide, not a copy. It explains when to call an external skill, how to install it and how to get good results. It contains none of the original skill's text; install the original to use it.

## What it does

AI coding agents often write web code the way it was written years ago: a JavaScript library for a dialog, a scroll listener for an animation, a hand-rolled drawer. Modern Web Guidance is a skill from the Chrome team that makes the agent look up a short, expert-written guide before it codes a web feature, so it reaches for what the browser can already do. Guides cover layout, CSS, forms, accessibility, performance, security and browser support, and the agent ends its reply by listing which guides shaped the code.

## When to use

- Use before building any page, site or app UI: portfolio pages, landing pages, dashboards, Returns Bench screens.
- Use on an older project to scan for outdated patterns and get a list of what to modernise.
- Use when a UI Library effect (UI-01 … UI-42) is being turned into real code, so it uses native features such as dialogs, popovers and scroll-driven animation where the browser supports them.
- Do not use for design work in Figma or for video; it only guides code.

## Routing

| Job | Call | Why |
| --- | --- | --- |
| Build a web feature the modern way | `modern-web-guidance` (search, then retrieve a guide) | Puts the right guide in the agent's context before it writes code |
| Find outdated code in a project | `modern-web-guidance legacy-scan` | Lists old patterns with the modern replacement |
| Build a Chrome extension | `chrome-extensions` (second skill in the same repo) | Extension-specific guides |

## Install

In Claude Code (recommended, keeps itself up to date):

```bash
npx modern-web-guidance@latest install
```

Or as a Claude Code plugin: `/plugin marketplace add GoogleChrome/modern-web-guidance`, then `/plugin install modern-web-guidance@googlechrome`.

To use the guide in the Claude app without Terminal, upload the zip of this folder in Settings → Capabilities → Skills. The lookups themselves run through `npx`, so they need Claude Code or another agent with a terminal.

Requirements: Node.js. Works offline after the first download; no API key.

## How to ask

- "Use Modern Web Guidance, then build a mobile navigation drawer for my portfolio."
- "Use Modern Web Guidance to scan this project for legacy patterns and list what to change first."
- "Build this modal with Modern Web Guidance and tell me which guides you used."

## Watch-outs

- It is a preview release; guides are still being added, so some features have no guide yet.
- Newer features may not work in every browser. Tell the agent which browsers you need to support.
- It shapes how code is written; it does not test the result. Check the page yourself or with Dev-07 Playwright CLI.

## Credit

`modern-web-guidance` by the Google Chrome team, Apache-2.0. Checked on 2026-11-21 at commit `64a6d70`.

## Copy-ready English prompt

```text
Use the modern-web-guidance skill. Before writing code, search for and read the guides that fit <feature>. Build it with modern, accessible browser features rather than extra libraries, make it work at 375px and 1440px, and finish with a list of the guides you used.
```
