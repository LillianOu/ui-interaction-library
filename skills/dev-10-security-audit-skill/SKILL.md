---
name: dev-10-security-audit-skill
description: Use when an app, API or website you built needs a security check before launch, before selling it, or after a big change. security-audit-skill routes to Cloudflare's official security-audit skill.
---
# Dev-10 — security-audit-skill

**Category:** 工具庫 / Tool Library · 開發與工作流 / Dev & Workflow
**Powered by:** [cloudflare/security-audit-skill](https://github.com/cloudflare/security-audit-skill) `security-audit` (MIT)

> This skill is a guide, not a copy. It explains when to call an external skill, how to install it and how to get good results. It contains none of the original skill's text; install the original to use it.

## What it does

security-audit-skill turns a coding agent into a security reviewer for a codebase. It works in stages: it maps the app, hunts for weak spots (sign-in, permissions, data leaks, injection, secrets, deployment set-up), then has separate helper agents try to confirm each finding, so you get a short list of real problems instead of a long list of guesses. Results come back in a structured, machine-readable form as well as a readable report.

## When to use

- Use before you launch or sell an app that stores customer or company data (for example Returns Bench).
- Use after adding sign-in, payments, file uploads or an API.
- Use when you have vibe-coded something and want to know what an attacker could do with it.
- Do not use on code you do not own or have permission to test.
- Do not treat it as a replacement for a professional penetration test when a client contract requires one.

## Routing

| Job | Call | Why |
| --- | --- | --- |
| Full audit of a repo | `security-audit` | Runs every stage and verifies findings |
| Plan which fixes to make first | `security-audit`, then Dev-02 Grill Me on the fix plan | Fix the confirmed, high-impact items first |
| Check the page still works after fixes | Dev-07 Playwright CLI | Security fixes can break flows |

## Install

In Claude Code:

```bash
npx skills add https://github.com/cloudflare/security-audit-skill --skill security-audit --global
```

Drop `--global` to install it for one project only. To use the guide in the Claude app without Terminal, upload the zip of this folder in Settings → Capabilities → Skills; the audit itself needs Claude Code, because it reads the whole repo and runs helper agents.

Requirements: a coding agent that can start helper agents (Claude Code can).

## How to ask

- "Run a security audit on this codebase and give me the confirmed findings, worst first."
- "Security audit the sign-in and file-upload parts of this app only."
- "Explain each finding in plain English and tell me what to fix first."

## Watch-outs

- A full audit reads a lot of code and uses many tokens. Point it at the parts that matter if the repo is large.
- Findings can still be wrong; read each one before changing code.
- The report can describe real weaknesses. Do not post it in a public repo or issue.

## Credit

`security-audit` by Cloudflare, MIT. Checked on 2026-11-21 at commit `c1c8a8c`.

## Copy-ready English prompt

```text
Use the security-audit skill on this repository. Focus on <sign-in / customer data / uploads / API>. Give me only verified findings, worst first, each with a plain-English explanation, how someone could exploit it, and the smallest safe fix. Do not change any code until I confirm.
```
