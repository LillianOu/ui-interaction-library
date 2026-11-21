---
name: dev-11-matt-pocock-skills
description: Use when building an app with a coding agent and you need to turn a chat into a build plan, try a quick prototype, fix a hard bug, review changes, learn a concept, or hand a chat over to a new session. Routes to Matt Pocock's to-spec, prototype, diagnosing-bugs, code-review, teach and handoff skills.
---
# Dev-11 — Matt Pocock Skills

**Category:** 工具庫 / Tool Library · 開發與工作流 / Dev & Workflow
**Powered by:** [mattpocock/skills](https://github.com/mattpocock/skills) `to-spec` · `prototype` · `diagnosing-bugs` · `code-review` · `teach` · `handoff` (MIT)

> This skill is a guide, not a copy. It explains when to call an external skill, how to install it and how to get good results. It contains none of the original skills' text; install the originals to use them.

## What it does

Matt Pocock's skill pack covers the whole build cycle with small, focused skills. This library already has four of them as their own entries: Dev-02 Grill Me (grill-me, grill-with-docs), Dev-03 Codebase Architecture and Dev-04 TDD. This entry covers the six others most useful for a designer building real products: plan, prototype, debug, review, learn and hand over.

## When to use

- Use when an idea has been talked through and needs to become a written build plan.
- Use when you want to see whether a UI or logic idea feels right before building it properly.
- Use when something is broken, failing or slow and quick fixes have not worked.
- Use before you merge or ship, to check the changes match the plan.
- Do not use for questioning a fuzzy idea; call Dev-02 Grill Me first, then come back here.

## Routing

| Job | Call | Why |
| --- | --- | --- |
| Turn the chat into a build plan | `to-spec` | Writes up what was decided, without another interview |
| Try an idea fast | `prototype` | A throwaway version that answers one design question |
| Fix a hard bug | `diagnosing-bugs` | A step-by-step loop: reproduce, narrow down, prove the cause, then fix |
| Check changes before shipping | `code-review` | Checks the code against your standards and the plan |
| Learn something while building | `teach` | Explains a concept inside your own project |
| Move to a fresh chat or agent | `handoff` | Packs the chat into a short brief another session can pick up |
| Questions before planning | Dev-02 Grill Me | Already in the library |
| Tidy a messy codebase | Dev-03 Codebase Architecture | Already in the library |
| Build test-first | Dev-04 TDD | Already in the library |

## Install

In Claude Code, add just these six:

```bash
npx skills@latest add mattpocock/skills
```

When it asks which skills to take, tick `to-spec`, `prototype`, `diagnosing-bugs`, `code-review`, `teach`, `handoff` and `setup-matt-pocock-skills`. Leave `grill-me`, `grill-with-docs`, `improve-codebase-architecture` and `tdd` ticked too if Dev-02 to Dev-04 are not installed yet.

Then run `/setup-matt-pocock-skills` once in each project. It asks where plans and tickets live (GitHub Issues or plain markdown files in the repo). Choose markdown files if you do not use GitHub Issues.

Or install the whole pack as a plugin: `/plugin marketplace add mattpocock/skills`, then `/plugin install mattpocock-skills@mattpocock`. Pick one method, not both, or every skill appears twice.

To use the guide in the Claude app without Terminal, upload the zip of this folder in Settings → Capabilities → Skills.

## How to ask

- "Use to-spec to turn what we decided into a build plan."
- "Use prototype to try two layouts for the returns screen. Throwaway code is fine."
- "Use diagnosing-bugs: the export button does nothing on mobile."
- "Use code-review on everything since this morning's commit."
- "Use handoff so I can carry on in a new chat."

## Watch-outs

- `to-spec` and `code-review` expect `/setup-matt-pocock-skills` to have been run; without it they ask where things go.
- `prototype` code is meant to be thrown away. Do not ship it.
- The pack changes often and has unfinished skills in an `in-progress` folder. Install only the named skills above.

## Credit

`mattpocock/skills` by Matt Pocock, MIT. Checked on 2026-11-21 at commit `5863806`.

## Copy-ready English prompt

```text
Use the to-spec skill to turn this conversation into a build plan for <feature>, saved as a markdown file in the repo. Then use prototype to build a quick throwaway version of the main screen so I can check it looks and feels right before we build it properly.
```
