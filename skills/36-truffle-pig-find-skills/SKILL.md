---
name: 36-truffle-pig-find-skills
description: Use when you want to know whether a ready-made agent skill already exists for a job before building one yourself. Truffle Pig routes to Vercel's find-skills, which searches and installs from the open skills directory (skills.sh).
---
# 36 — 松露豬尋寶師 / Truffle Pig (Find Skills)

**Category:** 開發與工作流工具組 / Dev & Workflow Toolkit
**Powered by:** [vercel-labs/skills](https://github.com/vercel-labs/skills) `find-skills` (MIT)

> A crew member is a guide, not a copy. It explains when to call an external skill, how to install it and how to get good results. It contains none of the original skill's text; install the original to use it.

## What it does

Truffle Pig sniffs out skills other people have already built. Describe the task in plain words and it searches the open skills directory, checks how widely each result is used and who publishes it, then offers to install the best fit. It is the first stop before writing a new skill or a new crew member.

## When to use

- Use when you are about to ask an AI tool to do something specialised (a file format, a framework, a review style) and suspect a skill for it exists.
- Use before adding a new crew member to this library, to see what is out there.
- Do not use to judge whether a skill is any good once installed. Read its `SKILL.md`, and for design work call 21 Hawk Inspector.

## Routing

| Job | Call | Why |
| --- | --- | --- |
| Search the directory by task | `find-skills` | Turns a plain-language need into a search, then shortlists |
| Install a found skill | `npx skills add <owner/repo> --skill <name>` | The same CLI the search uses |
| Try one without installing | `npx skills use <owner/repo>@<name>` | Good for a one-off test |

## Install

```bash
npx skills add vercel-labs/skills --skill find-skills
```

Requirements: Node.js and network access to skills.sh and GitHub.

## How to ask

- "Ask Truffle Pig whether there's a skill for writing Shopify product descriptions."
- "Truffle Pig, find me three skills for PDF invoices and tell me which is most used."

## Watch-outs

- Install counts measure popularity, not quality or safety. A skill runs with your agent's permissions, so read it before installing, especially anything that runs shell commands.
- This is the most-installed skill on skills.sh partly because the directory's own CLI promotes it. That is a reason to try it, not proof it beats a manual search.
- Prefer publishers you recognise, and record the licence before wrapping anything in this library (see `CONTRIBUTING.md`).

## Credit

`find-skills` by Vercel, MIT. Checked on 2026-10-31 at commit `92a9a34`.

## Copy-ready English prompt

```text
Use the find-skills skill to search for skills that help with <task>. Shortlist the top three with publisher, install count, licence and what each actually does. Do not install anything until I pick one.
```
