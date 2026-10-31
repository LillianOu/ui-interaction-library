---
name: 34-landing-page-generator
description: Use when a landing page needs to sell, not just look good — a conversion-ordered structure, real copy written from a proven framework, SEO metadata and ready React/Next.js + Tailwind sections. Landing Page Generator routes to alirezarezvani's landing-page-generator skill.
---
# 34 — Landing Page Generator
**Category:** 技能庫 / Skill Library · 設計 / Design
**Powered by:** [alirezarezvani/claude-skills](https://github.com/alirezarezvani/claude-skills) `landing-page-generator` (MIT)

> This skill is a guide, not a copy. It explains when to call an external skill, how to install it and how to get good results. It contains none of the original skill's text; install the original to use it.

## What it does

Landing Page Generator works on what a landing page says and in what order. The skill behind it collects a short brief (product, audience, pain, benefit, pricing), picks a copywriting framework, writes the actual words first, then builds the sections in a conversion-tested sequence: hero with several headline options, features, pricing, FAQ, social proof, call to action and footer. It outputs Next.js / React components styled with Tailwind, plus meta tags and structured data, and checks the page against an SEO and speed checklist.

## When to use

- Use when launching a product, course, app or service and the page must turn visitors into sign-ups or sales.
- Use when you have the product but not the words, or the words but no structure.
- Use when you want several headline options to test against each other.
- Do not use to set the visual style. Let Landing Page Generator write the structure and copy, then call 17 Taste Pack (or apply a 31 Awesome DESIGN.md DESIGN.md) for the look.
- Do not use for a one-off presentation mockup. Call 20 Huashu + Baoyu.

## Routing

| Job | Call | Why |
| --- | --- | --- |
| Full landing page: copy, structure, components, SEO | `landing-page-generator` | Copy first, then sections in a fixed conversion order |
| Pick the persuasion structure | `landing-page-generator` | Chooses PAS (problem, agitate, solve), AIDA (attention, interest, desire, action) or BAB (before, after, bridge) |
| Only a quick scaffold without the brief | its `landing_page_scaffolder.py` script | Plain Python, no extra packages |

## Install

```bash
npx skills add alirezarezvani/claude-skills --skill landing-page-generator
```

Or in Claude Code, install the whole product bundle: `/plugin marketplace add alirezarezvani/claude-skills`, then `/plugin install product-skills@claude-code-skills`.

Requirements: a React or Next.js project with Tailwind for the components. Python 3 only for the optional scripts.

## How to ask

- "Landing Page Generator: landing page for my 3PL returns app, aimed at warehouse managers, PAS framework, three pricing tiers."
- "Ask Landing Page Generator for five hero headline options for the AARVO.AI workshop, then build the page with the strongest."
- "Landing Page Generator, copy only: rewrite this page's sections in AIDA order."

## Watch-outs

- Its four built-in styles (dark SaaS, clean minimal, bold startup, enterprise) are generic by design. Keep Landing Page Generator's structure and words, and take the visual layer from your brand.
- It will happily invent testimonials, logos and numbers to fill sections. Replace every one with real proof or delete the section; fabricated social proof is worse than none.
- Output targets React / Next.js. For a plain HTML site, ask it to write the copy and section plan only.
- Copy written from a framework still needs your voice. Read it aloud before publishing.

## Credit

Original work by Alireza Rezvani, MIT. Checked on 2026-10-29 at commit `0496583` (repo release v2.14.3).

## Copy-ready English prompt

```text
Use the landing-page-generator skill.
Product: <name, one line>. Audience: <who>. Their pain: <problem>. Main benefit: <outcome>.
Pricing: <tiers or "none">. Framework: <PAS | AIDA | BAB | choose for me and say why>.
Write all copy first and show it to me. Give five hero headline options.
Use only real proof I provide: <testimonials, numbers, logos or "none — leave proof sections out">.
Then build the sections as <Next.js + Tailwind components | a section plan only>, with meta tags and FAQ structured data.
```
