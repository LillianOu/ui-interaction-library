---
name: 42-meerkat-lookout-reddit
description: Use when you want to find Reddit threads where people are genuinely asking for what you offer, and draft short, honest, disclosed replies you review and post yourself. Meerkat Lookout routes to doany.ai's reddit-automation skill.
---
# 42 — 狐獴瞭望員 / Meerkat Lookout (Reddit Automation)

**Category:** 開發與工作流工具組 / Dev & Workflow Toolkit
**Powered by:** [flowkit-labs/skills](https://github.com/flowkit-labs/skills) `reddit-automation` (MIT)

> A crew member is a guide, not a copy. It explains when to call an external skill, how to install it and how to get good results. It contains none of the original skill's text; install the original to use it.

## What it does

Meerkat Lookout stands up and scans the horizon. Given your product, buyer and a list of subreddits, it picks out the few threads where someone is clearly asking for help you can give, explains why each is worth answering, then drafts a two-or-three-sentence reply written from real experience. It only mentions your product when it truly answers the question, and always with disclosure.

## When to use

- Use to find real demand for a product such as AARVO Shop, VinoIQ or the returns app, and join those conversations honestly.
- Use as research: the threads it finds show how buyers describe their problem in their own words.
- Do not use to post automatically, run several accounts or seed fake praise. The skill refuses this, and Reddit bans it.

## Routing

| Job | Call | What you get |
| --- | --- | --- |
| Find and rank threads, draft replies | `reddit-automation` | Top three threads with a reason for each, plus short drafts for you to edit and post by hand |

## Install

```bash
npx skills add flowkit-labs/skills --skill reddit-automation
```

Requirements: nothing to install beyond the skill. It needs your product details up front; it reads posts you point it to and never signs in or posts.

## How to ask

- "Ask Meerkat Lookout to find this week's best threads for VinoIQ in r/wine and r/restaurateur."
- "Meerkat Lookout, draft a reply to this thread — no product mention unless it really fits."

## Watch-outs

- Ranked 10th by installs, but it is a marketing skill, not a design or coding one. It sits in this crew because it came from the same top-10 list.
- Each subreddit has its own self-promotion rules. Read them before posting, even with disclosure.
- The repo README gives `doany-skills/skills` as the install source; `flowkit-labs/skills` is where the code was checked. If one fails, try the other.
- Rewrite every draft in your own voice. Several near-identical replies read as spam.

## Credit

`reddit-automation` by doany.ai, MIT. Checked on 2026-10-31 at commit `0c9e2b6`.

## Copy-ready English prompt

```text
Use the reddit-automation skill. My product: <one line>. Buyer: <who>. Competitors: <names>. Subreddits: <list>. Find the three threads where I can genuinely help, say why for each, and draft a disclosed reply for each. I will post them myself.
```
