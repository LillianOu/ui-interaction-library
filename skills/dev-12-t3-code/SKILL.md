---
name: dev-12-t3-code
description: Use when you want to run Claude Code, Codex or another coding agent from a proper app window (desktop, web or phone) instead of Terminal. T3 Code routes to pingdotgg's open-source T3 Code app.
---
# Dev-12 — T3 Code

**Category:** 工具庫 / Tool Library · 開發與工作流 / Dev & Workflow
**Powered by:** [pingdotgg/t3code](https://github.com/pingdotgg/t3code) T3 Code app (MIT)

> This skill is a guide, not a copy. It explains when to use an external tool, how to install it and how to get good results. It contains none of the original's text.

## What it does

T3 Code is a free app that puts one clean chat window on top of the coding agents you already use: Claude Code, Codex, Cursor, OpenCode and others. It does not include a model or charge for tokens; it uses the agents signed in on your computer. You get the same agent power as Terminal, with readable messages, project threads, and the option to check on runs from a browser or your phone.

## When to use

- Use when Terminal feels hard to read and you want Claude Code in a normal app window.
- Use when you switch between Claude Code and Codex and want both in one place.
- Use to check on a long build from your phone.
- Pick T3 Code or Dev-13 Orca, not both. T3 Code is simpler (one chat window per job); Orca is for running several agents side by side.
- Do not use for work you can do in the Claude app itself; you only need T3 Code when a job needs Claude Code.

## Routing

| Job | Use | Why |
| --- | --- | --- |
| Run Claude Code without Terminal | T3 Code desktop app | Same agent, readable window |
| Try it before installing | `npx t3@latest` | Runs once without an install |
| Several agents at once on one project | Dev-13 Orca | Built for parallel agents |

## Install

macOS: `brew install --cask t3-code` · Windows: `winget install T3Tools.T3Code`, or download from the [releases page](https://github.com/pingdotgg/t3code/releases).

Then sign in to at least one agent once, for example `claude auth login` for Claude Code.

Requirements: Claude Code or Codex installed and signed in. Your normal subscription is used.

## How to ask

T3 Code is a window, not a skill. Open your project in it and talk to Claude Code as usual. Your library skills (for example Dev-09, Dev-10) still work inside it, because Claude Code loads them.

## Watch-outs

- It is early software (version 0.0.x); expect small bugs and frequent updates.
- Phone and browser access means your computer is reachable from elsewhere. Only turn on remote access on a network you trust, and follow its pairing steps.
- Agents still act on your files. Keep work in Git so changes can be undone.

## Credit

T3 Code by T3 Tools (pingdotgg), MIT. Checked on 2026-11-21 at commit `c1464d6`.

## Copy-ready English prompt

```text
(Inside T3 Code, in your project) Read AGENTS.md and the README first. Then <task>. Explain each change in plain English before you make it, and stop and ask me before deleting anything.
```
