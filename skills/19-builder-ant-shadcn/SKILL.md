---
name: 19-builder-ant-shadcn
description: Use when building a React or Next.js interface from ready-made, accessible components instead of hand-written markup, or applying a design system to shadcn/ui. Builder Ant routes to shadcn/ui's official shadcn skill.
---
# 19 — 螞蟻組件師 / Builder Ant (shadcn/ui)

**Category:** 設計工具組 / Design Toolkit
**Powered by:** [shadcn/ui](https://github.com/shadcn-ui/ui) `shadcn` (MIT)

> A crew member is a guide, not a copy. It explains when to call an external skill, how to install it and how to get good results. It contains none of the original skill's text; install the original to use it.

## What it does

Builder Ant assembles interfaces from shadcn/ui components: buttons, dialogs, forms, tables, sheets, charts and chat layouts. shadcn/ui copies each component's source into your project, so you own and can restyle it. The official skill knows the project's setup, adds components with the right command, follows the library's composition and form rules, and can turn a design spec into a shadcn theme.

## When to use

- Use when building app screens, dashboards, admin tools or forms in React, Next.js or Vite.
- Use when the project already has a `components.json` file (a shadcn project).
- Use when turning a design system or brand spec into a working component theme.
- Do not use for a static marketing page with no app logic; 17 Pearl Peacock or 20 Octo Studio fit better.
- Do not use outside React; shadcn/ui is React-only.

## Routing

| Job | Call | Why |
| --- | --- | --- |
| Start a new shadcn project or apply a preset | `shadcn` | Runs `shadcn init` with the right package manager |
| Add, fix or compose components | `shadcn` | Uses real components instead of custom markup |
| Apply a design system or brand spec | `shadcn` | Maps tokens onto the shadcn theme |

## Install

```bash
npx skills add shadcn/ui --skill shadcn
```

Requirements: Node and a React project. The skill runs the shadcn CLI (`npx shadcn@latest`, or the pnpm or bun equivalent).

## How to ask

- "Ask Builder Ant to build the returns dashboard: data table with filters, a detail sheet and a refund form."
- "Builder Ant: apply my design system to the shadcn theme."

## Watch-outs

- Components land as source in your repo. Review the diff before committing, as with any code.
- Default shadcn styling is recognisable. Pair Builder Ant with a direction from 17 Pearl Peacock so the result does not look like every other shadcn app.
- Interaction patterns 01–08 in this library describe behaviour shadcn does not cover (drag to reorder, fly-to-target and so on). Use them on top.

## Credit

Original work by shadcn, MIT licence. Checked on 2026-10-18 at commit `d2fba50`.

## Copy-ready English prompt

```text
Use the shadcn skill to build <screen> in this React project with shadcn/ui components only (no custom markup where a component exists). Include: <components and data>. Apply these design tokens: <colours, radius, fonts>. Cover loading, empty and error states, and make the layout work at 375px, 768px and 1440px.
```
