---
name: 61-cangjie-skill
description: Use when a book, course, talk, podcast or long video (with its text or transcript) should become a set of reusable Claude skills instead of a summary you never use again. Routes to kangarooking/cangjie-skill.
---
# 61 — cangjie-skill (仓颉)

**Category:** 學習庫 / Learning Library
**Powered by:** [kangarooking/cangjie-skill](https://github.com/kangarooking/cangjie-skill) (MIT)

> This skill is a guide, not a copy. It explains when to call an external skill, how to install it and how to get good results. It contains none of the original skill's text; install the original to use it.

## What it does

cangjie-skill reads a whole source (a book, course, interview, talk or long article) and pulls out the methods in it that you can actually reuse. Each method becomes its own small skill with when-to-use triggers, limits and steps, and each one is tested before it is kept. You also get an index showing how the skills connect and a readable digest of the whole source, so you can skip the full book when you only need the ideas.

## When to use

- Use when you have finished, or want the value of, a book on UX, product, business or AI workflow and want Claude to apply its methods in real work later.
- Use when a long YouTube talk or course has subtitles or a transcript and you want its frameworks as tools, not notes.
- Use when building AARVO.AI teaching content: the digest is a strong first draft for a script.
- Do not use without the real text. It will not distil a book from memory; get the PDF, EPUB, TXT, subtitles or transcript first.
- Do not use for a quick summary of a short article. Just ask Claude for a summary.

## Routing

| Job | Call | Why |
| --- | --- | --- |
| Book, course, talk or transcript → tested skill pack + digest | `cangjie-skill` | Runs the full extract → test → install pipeline |
| Get subtitles or audio from a video first | the author's `video-downloader` skill, or any transcript tool | cangjie-skill needs text, not video |

## Install

```bash
git clone https://github.com/kangarooking/cangjie-skill.git ~/.claude/skills/cangjie-skill
```

For one project only, clone it into `<project>/.claude/skills/cangjie-skill` (Claude Code) or `<project>/.cursor/skills/cangjie-skill` (Cursor).

Requirements: an agent tool that can run sub-agents (Claude Code, Cursor, OpenClaw). It runs several extraction passes in parallel and falls back to one at a time where parallel agents are not available. Large books take a long time and many tokens.

## How to ask

- "Use cangjie-skill on this PDF of *Don't Make Me Think* and install the resulting skills."
- "Distil this talk transcript into skills, then show me the digest first."
- "Turn this course transcript into skills I can use for my portfolio case studies."

## Watch-outs

- Output is only as good as the text. Scanned PDFs need OCR first; auto-generated subtitles need a quick clean-up.
- The generated skills install into your skills folder. Review the list before keeping all of them, so your skill list stays tidy.
- Mostly written in Chinese; outputs follow the language you ask for.
- Same author makes nuwa-skill (distils a person's thinking) and darwin-skill (improves skills over time). Its test files work with darwin-skill.

## Credit

Original work by kangarooking (袋鼠帝), MIT. Checked on 2026-11-01 at commit `a28de55`.

## Copy-ready English prompt

```text
Use the cangjie-skill skill on the attached book. Extract only methods I can reuse in design and product work, test each one, install the ones that pass, and give me the digest and the index of skills at the end.
```
