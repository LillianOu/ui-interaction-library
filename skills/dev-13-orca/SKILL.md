---
name: dev-13-orca
description: Use when you want several coding agents (Claude Code, Codex and others) working on the same project at once, each in its own copy, so you can compare results and keep the best. Orca routes to Stably AI's open-source Orca app.
---
# Dev-13 — Orca

**Category:** 工具庫 / Tool Library · 開發與工作流 / Dev & Workflow
**Powered by:** [stablyai/orca](https://github.com/stablyai/orca) Orca app (MIT)

> This skill is a guide, not a copy. It explains when to use an external tool, how to install it and how to get good results. It contains none of the original's text.

## What it does

Orca is a free desktop workspace for running many coding agents in parallel. Each job gets its own Git worktree (a separate working copy of the project), so agents do not overwrite each other. You see every agent's progress, compare their changes side by side and merge the one you like. It works with 30+ terminal agents, including Claude Code and Codex, and has phone apps for checking in.

## When to use

- Use when you want two agents to try the same task (for example two versions of a landing page) and pick the better one.
- Use when you have several separate tasks on one project and want them done at the same time.
- Pick Orca or Dev-12 T3 Code, not both. For one agent at a time, T3 Code is simpler.
- Do not use for small, single tasks; the set-up is more than the job needs.

## Routing

| Job | Use | Why |
| --- | --- | --- |
| Same task, several agents, pick the best | Orca parallel worktrees | Side-by-side diffs and merge |
| Several tasks at once | One Orca workspace per task | Agents stay out of each other's way |
| One agent in a friendly window | Dev-12 T3 Code | Lighter |

## Install

Download from [orca.dev/download](https://orca.dev/download), or on macOS: `brew install --cask stablyai/orca/orca`. Phone apps are on the App Store and Google Play.

Requirements: the project must be a Git repository, and at least one agent (for example Claude Code) installed and signed in. Your own subscriptions are used.

## How to ask

Orca is a workspace, not a skill. Open your repo, start a workspace per task, choose the agent, and type the task. Example: run "Build the hero section from UI-24" in two workspaces, one with Claude Code and one with Codex, then compare.

## Watch-outs

- Each parallel agent uses its own tokens. Two agents on one task costs roughly twice as much.
- Merging two agents' changes can conflict; merge one at a time.
- Keep remote and phone access paired only to your own devices.

## Credit

Orca by Stably AI, MIT. Checked on 2026-11-21 at commit `0c5714b`.

## Copy-ready English prompt

```text
(Same task in two Orca workspaces) Read AGENTS.md first. Build <feature> following <UI-NN / Design-NN>. Work only inside this worktree, commit when done, and summarise what you built and anything you were unsure about.
```
