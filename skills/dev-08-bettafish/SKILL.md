---
name: dev-08-bettafish
description: Use when you want a researched report on what people are saying about a brand, product, topic or market across news and social media, especially Chinese platforms. BettaFish routes to 666ghj's BettaFish multi-agent public-opinion analysis app.
---
# Dev-08 — BettaFish (微舆)

**Category:** 工具庫 / Tool Library · 開發與工作流 / Dev & Workflow
**Powered by:** [666ghj/BettaFish](https://github.com/666ghj/BettaFish) (GPL-2.0)

> This skill is a guide, not a copy. It explains when to use an external tool, how to install it and how to get good results. It contains none of the original's text or code; install the original to use it.

## What it does

BettaFish is a self-hosted app, not a Claude skill. You type a research question in plain language, such as "How do people talk about home wine preservation?", and a team of AI agents goes to work. One searches the web and news, one reads images and short videos, one digs through its own database of collected social posts and comments, and a "forum" moderator makes them debate before a report agent writes an interactive HTML report on sentiment, themes and trends. A built-in crawler (MindSpider) can collect posts and comments from platforms such as Weibo, Xiaohongshu, Douyin, Kuaishou and Bilibili.

## When to use

- Use for market research before a product or content push: what an audience likes, complains about and asks for.
- Use to compare how a brand, competitor or topic is discussed across Chinese and international platforms.
- Do not use for a quick question; ordinary web search in Claude is faster and free.
- Do not use for Reddit demand-finding; use Dev-06 Reddit Automation.

## Routing

| Job | Use | Why |
| --- | --- | --- |
| Full research report on a topic | Main app at `localhost:5000` | All agents plus the forum debate and final report |
| Quick web and news scan only | Query Engine standalone app | Cheaper; one agent, no crawler or database needed |
| Image and short-video analysis only | Media Engine standalone app | Multimodal look at video and image content |
| Collect fresh posts and comments | MindSpider crawler | Fills the database the Insight agent reads |

## Install

Needs Claude Code or a Terminal; there is nothing to upload to the Claude app.

```bash
git clone https://github.com/666ghj/BettaFish
cd BettaFish
cp .env.example .env   # then fill in the keys below
docker compose up -d
```

Then open `http://localhost:5000`.

Requirements: Docker (or Python 3.9+ and PostgreSQL/MySQL for a source install). API keys for an OpenAI-compatible model for each agent (one provider can serve all of them) and for a web-search service such as Tavily. Crawling a platform needs a logged-in account on that platform.

## How to ask

- "Use BettaFish to research how Chinese-speaking wine drinkers in Taiwan and Singapore talk about buying wine by the glass. Report themes, complaints and price sensitivity."
- "Use BettaFish's Query Engine only: what are people saying this month about AI tools for designers?"

## Watch-outs

- Cost: every report runs many model calls across several agents. Start with the Query Engine on one small question and check your API usage before running full reports.
- Crawling: scraping social platforms usually breaks their terms of use and can get the logged-in account limited or banned. Use a separate test account, keep volumes low, and skip the crawler when web search is enough.
- Privacy: collected comments are other people's posts. Use them for aggregate insight; do not republish them or profile individuals.
- Licence: GPL-2.0. Using it for your own research is fine; if you ship a modified version to others, your changes must be shared under GPL-2.0 too.
- Heavy setup: Docker, a database and many keys. Budget an afternoon for the first run.
- Reports read confidently. Spot-check the sources behind any claim before acting on it.

## Credit

BettaFish by 666ghj and contributors, GPL-2.0. Checked on 2026-11-16 at commit `b67928f`.

## Copy-ready English prompt

```text
Research question: <topic>. Audience: <who>. Platforms: <which>. Report the main themes, positive and negative sentiment with examples, unmet needs, and three opportunities for a small brand. List the sources behind each finding.
```
