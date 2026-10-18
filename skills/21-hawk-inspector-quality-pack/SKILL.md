---
name: 21-hawk-inspector-quality-pack
description: Use when a UI is built and needs checking before it ships: standards and accessibility, a scored critique, polish fixes or motion feel. Hawk Inspector routes to Vercel's web-design-guidelines, educlopez's ui-craft, pbakaus's impeccable and Emil Kowalski's emil-design-eng.
---
# 21 — 鷹眼質檢員 / Hawk Inspector (Quality Pack)

**Category:** 設計工具組 / Design Toolkit
**Powered by:** [vercel-labs/agent-skills](https://github.com/vercel-labs/agent-skills) `web-design-guidelines` (MIT) · [educlopez/ui-craft](https://github.com/educlopez/ui-craft) `ui-craft` (MIT) · [pbakaus/impeccable](https://github.com/pbakaus/impeccable) `impeccable` (Apache-2.0) · [emilkowalski/skills](https://github.com/emilkowalski/skills) `emil-design-eng` (MIT)

> A crew member is a guide, not a copy. It explains when to call an external skill, how to install it and how to get good results. It contains none of the original skills' text; install the originals to use them.

## What it does

Hawk Inspector is the crew's last stop: nothing ships until it has looked. The four skills check different layers, from hard rules to how an interface feels, so they work as a ladder rather than four versions of the same review.

## When to use

- Use after building a page, screen or component and before showing it to a client or shipping it.
- Use when a UI "feels off" and you cannot say why.
- Use when you want a quality score you can track or block a pull request on.
- Do not use to choose a visual direction from scratch. Call 17 Pearl Peacock.

## Routing

Climb the ladder in order; stop when the work is good enough for its purpose.

| Step | Job | Call | What you get |
| --- | --- | --- | --- |
| 1 | Standards and accessibility check | `web-design-guidelines` | Terse `file:line` findings against Vercel's Web Interface Guidelines, fetched fresh each run |
| 2 | Scored critique | `ui-craft` | A 0–100 score and findings tagged by business impact, based on usability heuristics and design laws; optional CI gate |
| 3 | Fix and polish | `impeccable` | Commands such as audit, polish, harden, typeset, quieter and bolder that make the changes |
| 4 | Motion and feel | `emil-design-eng` | Review of animation choices, easing, timing and the small details that make UI feel right |

## Install

```bash
npx skills add vercel-labs/agent-skills --skill web-design-guidelines
npx skills add educlopez/ui-craft --skill ui-craft
npx impeccable install            # run from the project root, then /impeccable init in your agent
npx skills@latest add emilkowalski/skills --skill emil-design-eng
```

Requirements: `web-design-guidelines` needs web access to fetch the guidelines. `ui-craft` also offers a standalone CLI that wires up its review agents and MCP quality gates; the skill alone is enough to start. `impeccable` downloads its engine once on first run.

## How to ask

- "Ask Hawk Inspector to run steps 1 and 2 on the checkout page."
- "Hawk Inspector, polish: fix what the audit found on my portfolio home page."
- "Hawk Inspector, motion only: review the animations in skill 08."

## Watch-outs

- `ui-craft` and `impeccable` both describe themselves as full design systems and overlap with 17 Pearl Peacock. Inside this crew, use them for checking and fixing, not for setting direction.
- A score is a signal, not a verdict. Read the findings; a 90 with a broken keyboard flow is still broken.
- Pair step 4 with the motion skills 09–13 in this library, which already carry reduced-motion rules.

## Credit

`web-design-guidelines` by Vercel, MIT, checked at commit `063bee9`. `ui-craft` by Eduardo Calvo, MIT, checked at commit `eb88d0a`. `impeccable` by Paul Bakaus, Apache-2.0, checked at commit `08d5b47`. `emil-design-eng` by Emil Kowalski, MIT, checked at commit `2d22863`. Checked on 2026-10-18.

## Copy-ready English prompt

```text
Review <files or URL> in four passes. 1) Use web-design-guidelines and list findings as file:line. 2) Use ui-craft to score the screen 0-100 and tag each finding by business impact. 3) Use impeccable to fix every blocker and friction item, then re-score. 4) Use emil-design-eng to review the motion and interaction feel. Finish with a short before/after summary.
```
