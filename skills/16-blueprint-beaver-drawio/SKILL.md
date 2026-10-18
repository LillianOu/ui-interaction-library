---
name: 16-blueprint-beaver-drawio
description: Use when a system, data model, process or user flow needs an editable diagram that stays in sync with code and lives in version control. Blueprint Beaver routes to Agents365-ai/drawio-skill (editable .drawio files).
---
# 16 — 河狸藍圖師 / Blueprint Beaver (draw.io)

**Category:** 設計工具組 / Design Toolkit
**Powered by:** [Agents365-ai/drawio-skill](https://github.com/Agents365-ai/drawio-skill) (MIT)

> A crew member is a guide, not a copy. It explains when to call an external skill, how to install it and how to get good results. It contains none of the original skill's text; install the original to use it.

## What it does

Blueprint Beaver builds engineering diagrams as real `.drawio` files you can open and edit in draw.io (diagrams.net), not flat pictures. It can draw from a description or read code, infrastructure config, SQL and API schemas and turn them into architecture, UML, ERD, sequence, BPMN, network and swimlane diagrams. Because the file is text, it can be committed and updated as the code changes.

## When to use

- Use when explaining how an app is built: services, databases, APIs, integrations.
- Use for a database diagram from a schema, or a process map such as a warehouse returns flow.
- Use when the diagram must be edited later by you or a developer.
- Do not use for screen layouts. Call 15 Sketch Squirrel.
- Do not use when a quick Mermaid diagram in a README is enough; that is lighter and needs no install.

## Routing

| Job | Call | Why |
| --- | --- | --- |
| New diagram from a description | `drawio-skill` | Authors an editable `.drawio` file |
| Diagram from code, SQL, IaC or an API schema | `drawio-skill` | Reads the source and lays out the diagram |
| Update an existing diagram after code changes | `drawio-skill` | Edits the file in place and keeps element identities stable |

## Install

```bash
npx skills add Agents365-ai/drawio-skill -g
```

Requirements: Python 3. Optional: the draw.io desktop app (`brew install --cask drawio` on macOS) for PNG, SVG and PDF export, and Graphviz for automatic layout. The skill is set to manual invocation, so call it by name.

## How to ask

- "Ask Blueprint Beaver to diagram my returns app: scanner, web app, Supabase database and the courier API."
- "Blueprint Beaver: draw an ERD from this schema.sql."

## Watch-outs

- It does not trigger on its own. Say "draw.io" or name the skill.
- Without the desktop app it can still write the `.drawio` file; only image export needs the app.
- Check labels against the real system. A diagram generated from old code will look confident and be wrong.

## Credit

Original work by Agents365-ai, MIT licence. Checked on 2026-10-18 at commit `5727082`.

## Copy-ready English prompt

```text
Use the drawio-skill to create an editable .drawio <architecture | ERD | sequence | swimlane> diagram of <system>. Components: <list>. Connections: <who calls whom, with protocols or data>. Group by <layer or team>, label every arrow, and export a PNG preview alongside the .drawio file.
```
