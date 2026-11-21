---
name: content-02-sherlock
description: Use when choosing or protecting a brand handle and you need to know on which social sites a username is already taken. Sherlock routes to the Sherlock Project's open-source username checker.
---
# Content-02 — Sherlock

**Category:** 工具庫 / Tool Library · 內容與社群 / Content & Social
**Powered by:** [sherlock-project/sherlock](https://github.com/sherlock-project/sherlock) Sherlock (MIT)

> This skill is a guide, not a copy. It explains when to use an external tool, how to install it and how to get good results. It contains none of the original's text.

## What it does

Sherlock checks a username across hundreds of websites and social networks and lists where an account with that name exists. For a brand, that answers two questions fast: is the handle free everywhere you want it, and has someone else already taken it (or copied your brand) on another platform.

## When to use

- Use before launching a brand or channel, to find a handle that is free on every platform you need.
- Use now and then to spot accounts that copy or squat on your brand name.
- Do not use to look up, track or profile private people. Use it on your own names and brand names only.

## Routing

| Job | Use | Why |
| --- | --- | --- |
| Is my handle free everywhere? | `sherlock <handle>` | Lists sites where it is taken |
| Check several name options | `sherlock name1 name2 name3` | Compare in one run |
| Write the bio once the handle is set | Content-01 (`ig-profile`) | Profile and bio skills |

## Install

In Claude Code or any terminal:

```bash
pipx install sherlock-project
```

Or with Docker: `docker run -it --rm sherlock/sherlock <handle>`.

Requirements: Python (pipx installs it in its own space).

## How to ask

- "Run Sherlock on aarvo, aarvoai and aarvo.kids and tell me which sites have each name free."
- "Use Sherlock to check if anyone else is using my brand handle on other platforms."

## Watch-outs

- "Found" means an account exists with that name, not that it belongs to anyone in particular.
- Results can be wrong when a site changes or adds a captcha; open the links to confirm.
- Using it to find or follow a real person can break laws and platform rules. Keep it to brand names you own or are choosing.

## Credit

Sherlock by the Sherlock Project, MIT. Checked on 2026-11-21 at commit `c588d7c`.

## Copy-ready English prompt

```text
Use Sherlock to check these brand handle options: <name1>, <name2>, <name3>. For each, list the platforms where it is taken and where it looks free, focusing on Instagram, Threads, TikTok, YouTube, X, Pinterest and Etsy. Then recommend the option that is free on the most of those.
```
