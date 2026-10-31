---
name: 38-codebase-architecture
description: Use when an existing codebase has grown messy and you want concrete refactoring suggestions, shown as a visual report you can choose from. Codebase Architecture routes to Matt Pocock's improve-codebase-architecture.
---
# 38 — Codebase Architecture
**Category:** 技能庫 / Skill Library · 開發與工作流 / Dev & Workflow
**Powered by:** [mattpocock/skills](https://github.com/mattpocock/skills) `improve-codebase-architecture` (MIT)

> This skill is a guide, not a copy. It explains when to call an external skill, how to install it and how to get good results. It contains none of the original skill's text; install the original to use it.

## What it does

Codebase Architecture looks at how your code is woven together and finds places where the same rule lives in several files, or where a module exposes a lot but does little. It looks hardest at the parts you have changed most recently, presents the opportunities as an HTML report with before-and-after diagrams, then interviews you about whichever one you pick. Example: a "cancel at least 2 hours ahead" rule copied into the web, mobile and admin code, moved into one place.

## When to use

- Use when a vibe-coded project has started to fight back: fixing one thing breaks another, or the AI keeps editing the wrong file.
- Use before handing a project to someone else, or before a big new feature.
- Do not use on an empty project. Plan first with 37 Grill Me.

## Routing

| Job | Call | What you get |
| --- | --- | --- |
| Find and rank refactoring opportunities | `improve-codebase-architecture` | A visual HTML report of candidates, then a guided discussion of the one you choose |

## Install

It relies on two helper skills from the same repo and the grilling interview used by 37.

```bash
npx skills@latest add mattpocock/skills --skill codebase-design
npx skills@latest add mattpocock/skills --skill grilling
npx skills@latest add mattpocock/skills --skill domain-modeling
npx skills@latest add mattpocock/skills --skill improve-codebase-architecture
```

Requirements: a git repository with some history (it reads recent commits to find hot spots). User-invoked: call it by name.

## How to ask

- "/improve-codebase-architecture"
- "Ask Codebase Architecture to look at the returns app, focusing on the scanning flow."

## Watch-outs

- It proposes; it does not refactor on its own. Treat the report as a menu, then make each change as a separate, tested step (39 TDD).
- Name a focus area on large repos, or it spends time on code that does not matter to you.
- The report describes ideas, not measured gains. Check the suggestion against how the app is really used.

## Credit

`improve-codebase-architecture`, `codebase-design`, `grilling` and `domain-modeling` by Matt Pocock, MIT. Checked on 2026-10-31 at commit `a496f55`.

## Copy-ready English prompt

```text
Use the improve-codebase-architecture skill on this repo. Focus on <area>. Show the candidates as an HTML report ranked by how much they would simplify future changes, then wait for me to pick one before discussing it.
```
