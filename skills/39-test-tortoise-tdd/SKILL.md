---
name: 39-test-tortoise-tdd
description: Use when you want an AI tool to build a feature or fix a bug test-first, so the code is checked by tests that survive later changes. Test Tortoise routes to Matt Pocock's tdd skill.
---
# 39 — 烏龜測試師 / Test Tortoise (TDD)

**Category:** 開發與工作流工具組 / Dev & Workflow Toolkit
**Powered by:** [mattpocock/skills](https://github.com/mattpocock/skills) `tdd` (MIT)

> A crew member is a guide, not a copy. It explains when to call an external skill, how to install it and how to get good results. It contains none of the original skill's text; install the original to use it.

## What it does

Slow and steady. Test Tortoise makes the AI write a failing test first, then just enough code to pass it, one small step at a time. It agrees with you up front on where tests should sit (the public edges of the code, not its internals), so the tests describe what the app does and keep passing when the code underneath is rewritten.

## When to use

- Use for logic that must be right: prices, stock counts, dates, permissions, anything in the 3PL returns flow.
- Use when fixing a bug, so a test proves it is fixed and stays fixed.
- Do not use for pure visual work such as layouts and animations; check those with 21 Hawk Inspector and the demos in this library.

## Routing

| Job | Call | What you get |
| --- | --- | --- |
| Build or fix test-first | `tdd` | A red-then-green loop, agreed test boundaries, and guidance on what makes a test worth keeping |

## Install

```bash
npx skills@latest add mattpocock/skills --skill tdd
```

Requirements: a project with a test runner (for example Vitest, Jest or pytest). The skill does not install one for you.

## How to ask

- "Ask Test Tortoise to add the refund calculation, test-first."
- "Use tdd to fix the bug where returned items double-count."

## Watch-outs

- It will ask you to confirm which boundaries to test before writing any test. Answer it; that step is where most of the value is.
- Slower than letting the AI write code freely. Use it where a wrong answer costs money or trust, not for throwaway prototypes.
- A passing suite only proves what the tests check. Read the test names: they should read like a list of things the app can do.

## Credit

`tdd` by Matt Pocock, MIT. Checked on 2026-10-31 at commit `a496f55`.

## Copy-ready English prompt

```text
Use the tdd skill to build <feature>. First propose which public interfaces we should test and what each test would catch, and wait for my OK. Then work in small red-green steps and show me the test list at the end.
```
