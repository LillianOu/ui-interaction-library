---
name: content-01-instagram-agent-skill
description: Use when planning, writing or checking Instagram content (Reels scripts and hooks, captions, carousels, stories, comments, DMs, profile, weekly plan, repurposing, post-mortems). Routes to the fourteen ig-* skills in instagram-agent-skill.
---
# Content-01 — instagram-agent-skill

**Category:** 工具庫 / Tool Library · 內容與社群 / Content & Social
**Powered by:** [GoldenSharkStudio/instagram-agent-skill](https://github.com/GoldenSharkStudio/instagram-agent-skill) (MIT)

> This skill is a guide, not a copy. It explains when to call an external skill, how to install it and how to get good results. It contains none of the original skill's text; install the original to use it.

## What it does

A set of fourteen Claude skills that cover the writing side of running an Instagram account, from the Reel script to the reply under the post. Every skill reads one voice file about you, so the output sounds like you. Five small Python tools run on your own machine to score hooks, time scripts, lint captions and clean AI-sounding text. Nothing is posted for you: each skill ends with copy-ready text that you post yourself.

## When to use

- Use when you have an idea and want a Reel script with tested hooks, on-screen text and a timed beat sheet before you film.
- Use for captions, carousel copy, story sequences, comment and DM replies, a profile rewrite, a weekly posting plan, or turning one long video into a week of posts.
- Use when a draft sounds like AI and you want it cleaned and checked.
- Do not use to make the video itself. Call Video-01 HyperFrames Video or Video-03 OpenFilm, or Video-05 Sena & Pudding Reel Builder for that series.
- Do not use to post, follow or DM automatically. It is built not to.

## Routing

| Job | Call | Why |
| --- | --- | --- |
| First run, once | `/ig-setup` | Builds your voice file and sets the language every other skill uses |
| Reel from an idea | `/ig-reel` | Three hooks from 30 formulas, scored, then script, on-screen text and beat sheet |
| What works in your niche | `/ig-viral` | Ranks other accounts' Reels against their own normal and names the hook formula |
| Caption | `/ig-caption` | Checks the first 125 characters, the part the feed shows before "more" |
| Carousel | `/ig-carousel` | Cover, slide copy and 1080 × 1350 files |
| Stories | `/ig-story` | A daily story sequence, which sticker does which job, and a DM funnel |
| Profile | `/ig-profile` | Scores your profile out of 100 and rewrites the weakest parts first |
| Week plan | `/ig-plan` | What to post, which format, when, and accounts to engage with |
| Make it sound human | `/ig-human` | Cleans AI tells from a draft and scores the result |
| Comment on others' posts | `/ig-comment` | Picks a comment type to fit the post |
| Replies under your post | `/ig-reply` | Sorts the comments and answers the important ones first |
| DMs | `/ig-dm` | Keyword reply, first message, collab pitch and follow-ups |
| One long piece into many | `/ig-repurpose` | A video, podcast or newsletter into standalone Reels and carousels |
| Review what you posted | `/ig-audit` | Ranks your past posts by how far they beat your normal, and by sends per reach |

## Install

**In the Claude app (no Terminal, about 5 minutes):**

1. Download the repo as a ZIP from [GoldenSharkStudio/instagram-agent-skill](https://github.com/GoldenSharkStudio/instagram-agent-skill) (green **Code** button → **Download ZIP**) and unzip it.
2. In the `skills/` folder, zip each `ig-*` folder on its own (for example `ig-reel.zip`).
3. In Claude, open **Settings → Capabilities** and turn on **Code execution and file creation**.
4. Go to **Settings → Customize → Skills → Add**, and upload the zips. Start with `ig-setup`, `ig-reel`, `ig-caption`, `ig-story` and `ig-dm`.
5. In a new chat, say: "Use ig-setup", then paste three of your own captions.

**In Claude Code, as a plugin:**

```
/plugin marketplace add GoldenSharkStudio/instagram-agent-skill
/plugin install instagram-agent
```

Or copy the skill folders:

```bash
git clone https://github.com/GoldenSharkStudio/instagram-agent-skill.git
cp -r instagram-agent-skill/skills/ig-* ~/.claude/skills/
```

Then run `/ig-setup` once (about ten minutes). It writes `~/.claude/instagram/voice.md`.

Requirements: Python 3 for the five scoring tools; no packages, network, account or API key. Pasting a single `SKILL.md` into a chat works without Claude Code, but loses the Python tools, which matter most for `/ig-reel` and `/ig-human`.

## How to ask

- "/ig-reel: a 30-second Reel about why my kitten copies everything I say."
- "/ig-caption this, keywords: learn English, daily phrases."
- "/ig-repurpose this YouTube transcript into five Reels and two carousels."

## Watch-outs

- **Languages: English and Brazilian Portuguese only.** There is no Chinese. Use it for English posts; for Traditional Chinese posts the hook scores and the humanizer do not apply.
- The hook score catches weak hooks well but cannot pick the winner between two decent ones. The author's own test says so. Kill the bad hooks with it, then trust your Reels' retention data.
- The hook formulas were tested on YouTube Shorts, not Instagram Reels.
- The AI-text checks are local rules, not real detector services.
- `/ig-viral` reads Reels with you in your own browser at human speed. Do not turn it into a scraper; that breaks Instagram's Terms and gets accounts restricted.
- Changing fast: the repo went from 13 skills and 26 formulas to 14 and 30 within weeks, and many copies of the older version are on GitHub. Install from the link above.

## Credit

instagram-agent-skill, MIT, copyright Jake Schincariol (per its licence). Checked on 2026-11-07 at commit `6a28b3b`.

## Copy-ready English prompt

```text
Use the ig-reel skill. Read my voice.md first. Idea: <one-line idea>. Target length <seconds>s. Give me three hooks with their scores, pick the strongest, then the script, on-screen text and timed beat sheet. Flag any hook with a dealbreaker. Do not post anything.
```
