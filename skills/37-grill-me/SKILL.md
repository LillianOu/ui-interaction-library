---
name: 37-grill-me
description: Use when an idea, brief or plan is still fuzzy and you want to be questioned hard before anything gets built. Grill Me routes to Matt Pocock's grill-me (questions only) and grill-with-docs (questions plus a glossary and decision records).
---
# 37 — Grill Me + Grill with Docs
**Category:** 技能庫 / Skill Library · 開發與工作流 / Dev & Workflow
**Powered by:** [mattpocock/skills](https://github.com/mattpocock/skills) `grill-me` · `grill-with-docs` (MIT)

> This skill is a guide, not a copy. It explains when to call an external skill, how to install it and how to get good results. It contains none of the original skills' text; install the originals to use them.

## What it does

Grill Me digs. Instead of building from a one-line request such as "make a booking website", it interviews you in rounds, one layer of decisions at a time, offering a recommended answer to each question, until the plan has no soft spots. One version stops at a shared understanding; the other also writes down the project's vocabulary and key decisions as it goes.

## When to use

- Use at the very start of an app, site or feature, before any design or code.
- Use when a client brief is vague and you need to find out what they actually mean.
- Do not use once the plan is settled and you need architecture advice on existing code. Call 38 Codebase Architecture.

## Routing

These two are near-duplicates: both run the same underlying interview. Pick one.

| Job | Call | What you get |
| --- | --- | --- |
| Stress-test a plan, nothing written down | `grill-me` | A sharper plan in the chat |
| Stress-test a plan and keep a record | `grill-with-docs` | The same interview plus a `GLOSSARY.md` of project terms and short decision records (ADRs) in `docs/adr/` |

For anything you will build over more than a day, prefer `grill-with-docs`: the glossary keeps later AI sessions using the same words you agreed on.

## Install

Both are thin wrappers around helper skills in the same repo, so install the helpers too or they will do nothing.

```bash
npx skills@latest add mattpocock/skills --skill grilling
npx skills@latest add mattpocock/skills --skill grill-me
# for grill-with-docs, also:
npx skills@latest add mattpocock/skills --skill domain-modeling
npx skills@latest add mattpocock/skills --skill grill-with-docs
```

Or install the whole collection in Claude Code: `claude plugin install mattpocock-skills@claude-plugins-official`.

Requirements: none beyond an agent that supports skills. Both are user-invoked: call them by name, they will not start on their own.

## How to ask

- "/grill-me — I want to build a returns app for my warehouse."
- "Ask Grill Me to grill my portfolio site plan, with docs."

## Watch-outs

- Expect many rounds. Answer the questions you can, say "your call" on the rest, and it will move on.
- The interview is only as good as your answers. If you say "whatever's standard", you get a standard plan.
- `grill-with-docs` writes files into your repo. Run it inside the project folder, not a scratch chat.

## Credit

`grill-me`, `grill-with-docs`, `grilling` and `domain-modeling` by Matt Pocock, MIT. Checked on 2026-10-31 at commit `a496f55`.

## Copy-ready English prompt

```text
Use the grill-with-docs skill. Here is my idea: <one or two sentences>. Interview me in rounds until we agree on scope, users, the core flow and what is out of scope. Record our terms in GLOSSARY.md and any hard-to-reverse decision as an ADR.
```
