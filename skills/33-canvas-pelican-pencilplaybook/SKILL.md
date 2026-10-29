---
name: 33-canvas-pelican-pencilplaybook
description: Use when designing on a Pencil.dev canvas with an AI agent and you want consistent tokens, tidy screen placement and opinionated perceptual UI defaults instead of ad-hoc values. Canvas Pelican routes to Steve Barclay's PencilPlaybook skill, which drives Pencil.dev through its MCP tools.
---
# 33 — 鵜鶘畫板師 / Canvas Pelican (PencilPlaybook)

**Category:** 設計工具組 / Design Toolkit
**Powered by:** [stevembarclay/pencilplaybook](https://github.com/stevembarclay/pencilplaybook) (MIT)

> A crew member is a guide, not a copy. It explains when to call an external skill, how to install it and how to get good results. It contains none of the original skill's text; install the original to use it.

## What it does

Canvas Pelican works on a design canvas, not in code. Pencil.dev is a design tool whose `.pen` files an agent can read and edit through MCP. PencilPlaybook gives the agent a fixed routine for that: set up your design tokens once (from a preset or a short questionnaire), load them into every file, place new screens without overlapping old ones, and apply a table of perception-based defaults for things like disabled states, hover contrast, text on dark backgrounds, large-type letter spacing and touch target size. It also carries ready layouts for common screens: dashboard, list, detail, marketing page, modal, wizard, mobile, form and empty state.

## When to use

- Use when you design in Pencil.dev and want the agent to produce screens that share one token set.
- Use when you want quick, consistent first layouts for standard screen types on a canvas, then refine them by hand.
- Use when pushing a token change (a new accent colour, a new type scale) across every screen in a `.pen` file.
- Do not use if you do not use Pencil.dev; almost none of it applies elsewhere. For Figma, use the Figma plugin skills; for code, call 17 Pearl Peacock.
- Do not use to find a palette for a product type. Call 18 Magpie Muse, then feed the result into the setup step.

## Routing

| Job | Call | Why |
| --- | --- | --- |
| First-time brand setup on a canvas | `pencilplaybook` (setup) | Pick one of seven presets or answer six questions; writes your tokens into the skill |
| Lay out a new screen of a standard type | `pencilplaybook` | Uses its built-in layout recipes, then applies the token set |
| Apply a token change across the file | `pencilplaybook` | Its propagation routine updates every screen in one pass |
| Pull a style guide out of an existing file | `pencilplaybook` | Reads the canvas and writes the tokens it finds |

## Install

```bash
# all projects
git clone https://github.com/stevembarclay/pencilplaybook ~/.claude/skills/pencilplaybook
# or one project
git clone https://github.com/stevembarclay/pencilplaybook .claude/skills/pencilplaybook
```

Use the lower-case folder name shown above: the skill refers to its own setup file by that path, and the README's mixed-case folder name can break on Linux.

Requirements: Pencil.dev installed and open, with its MCP server connected to your agent.

## How to ask

- "Canvas Pelican: run setup with the Ember preset, then lay out a dashboard and an empty state for the returns app."
- "Ask Canvas Pelican to change our accent to #0089A8 across every screen in this file."
- "Canvas Pelican, pull a style guide from this .pen file."

## Watch-outs

- Small one-person project (about 50 stars at the time of checking). Expect rough edges and slow updates.
- The perceptual rules are confident, specific numbers, but the repo gives little evidence for them. Treat them as sensible defaults and check contrast with 21 Hawk Inspector.
- The repo also contains the author's own development skills in a hidden folder. Clone only the skill, and do not install those by accident.
- A canvas design is not a build. Move to 19 Builder Ant or 20 Octo Studio when the screens are settled.

## Credit

Original work by Steve Barclay, MIT. Checked on 2026-10-29 at commit `b732429` (v1.2.0).

## Copy-ready English prompt

```text
Use the pencilplaybook skill with the open Pencil.dev file.
If setup has not been run, run it with the <Midnight | Ember | Grove | Bloom | Volt | Material 3 | Minimal> preset, or ask me the setup questions.
Then create these screens for <product>: <screen types>. Place them in a new row without overlapping existing frames.
Use only the token set. When done, list any value you had to hard-code and why.
```
