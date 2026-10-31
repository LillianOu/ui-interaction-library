---
name: 15-wireframer
description: Use when an idea needs a rough, clickable low-fidelity prototype before any visual design, so people judge structure and flow rather than colours. Wireframer routes to agilek/wireframer-skill (Balsamiq-style hand-drawn wireframes).
---
# 15 — Wireframer
**Category:** 技能庫 / Skill Library · 設計 / Design
**Powered by:** [agilek/wireframer-skill](https://github.com/agilek/wireframer-skill) (MIT)

> This skill is a guide, not a copy. It explains when to call an external skill, how to install it and how to get good results. It contains none of the original skill's text; install the original to use it.

## What it does

Wireframer turns a description of an app or site into a hand-drawn, Balsamiq-style prototype you can click through. It is deliberately ugly: graph-paper background, sketchy components, placeholder images. That keeps a stakeholder conversation on layout, content and flow instead of fonts and colours. It is the first step in the design workflow.

## When to use

- Use when starting a new product, app screen set or website and the structure is not settled yet.
- Use when preparing a concept for a client or stakeholder who will otherwise fixate on visual polish.
- Use when mapping a user flow across several screens (onboarding, checkout, a returns process).
- Do not use for a polished mockup. Call 17 Taste Pack for visual direction, or 20 Huashu + Baoyu for a high-fidelity prototype.
- Do not use for a system or architecture diagram. Call 16 draw.io.

## Routing

| Job | Call | Why |
| --- | --- | --- |
| Clickable lo-fi prototype of one or more screens | `wireframer` | Produces a single self-contained page with working navigation between screens |

## Install

```bash
npx skills add agilek/wireframer-skill
```

Requirements: none beyond a browser to open the result. On first use in a project, the skill writes its style rules into the project's agent context file so later sessions keep the same look; review that change before committing it.

## How to ask

- "Ask Wireframer to wireframe the onboarding flow for my returns app: scan, condition check, refund decision."
- "Wireframer: lo-fi prototype of a portfolio site with home, case study and contact screens."

## Watch-outs

- Name every screen and the action that moves between them. Vague briefs give vague flows.
- Copy in the wireframe is placeholder-level. Rewrite it before user testing.
- Keep the output as a reference. Do not grow it into production code; rebuild the chosen structure with 19 shadcn/ui or 20 Huashu + Baoyu.

## Credit

Original work by agilek, MIT licence. Checked on 2026-10-18 at commit `22ed714`.

## Copy-ready English prompt

```text
Use the wireframer skill to build a clickable low-fidelity prototype of <product>. Screens: <list each screen and its purpose>. Navigation: <which control on which screen leads where>. Keep it hand-drawn and grey; focus on structure, content hierarchy and flow, not visual design. Include realistic placeholder content for <audience>.
```
