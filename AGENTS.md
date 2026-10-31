# Agent Instructions — Lilian O. Skill Library

These rules apply to Claude, Claude Code, Codex and any other AI agent working in this repo or using it as a reference.

## Start here

1. Read [`README.md`](README.md). It is the Skill Library index: UI Library, Tool Library (Design, Dev & Workflow, Video & Media), Learning Library and References.
2. Pick the entry that fits the job, then read its `skills/<category>-<NN>-<name>/SKILL.md` in full before building. Never build from the one-line summary in the README.
3. For a UI Library entry, open its demo page in `demo/` too and match its behaviour.
4. For a guide skill, install the original tool with the commands in its `SKILL.md`, then use it as the guide describes.
5. Name the entry IDs you used in your reply (for example UI-07, Design-13).

## Naming

Use each tool's real name. Do not invent character, animal or nickname names for skills.

## Adding to the Library

Whenever Lilian gives you a new skill, tool or link to add:

1. Tell her straight away, before adding it: which section (UI Library, Tool Library, Learning Library or References), which category, and the ID it will get (that category's next number, from "Next numbers" in the README). Example: "Tool Library → Design → Design-14".
2. If it overlaps an existing entry, say which one and suggest adding it there instead.
3. Credit the source: link the original, name the author and licence, and record the date and commit checked. For anything inspired by a video or post, name the creator. If the source is unknown, ask rather than guess.
4. Follow [`CONTRIBUTING.md`](CONTRIBUTING.md) and update the README index, "Next numbers" and `CHANGELOG.md` in the same commit. Commit as `Lilian O. <lillianou2000@gmail.com>`.

## Lilian's own preferences

Lilian keeps a profile of how she works and what she wants in her private repo `LillianOu/my-dna`. If you have access to it, read it before starting larger work; it is more current than anything here. Do not copy its contents into this public repo.

## Game UI work

For any game UI design task, read [`game-ui-references.md`](game-ui-references.md) first. Use the sites it lists for reference and pick the source that fits the job (layout, style, motion, or assets). Only copy assets marked ✅ into this repo, and put them in `game-assets/` with their licence file. Never download or commit screenshots or artwork from sites marked ❌.

## Never commit

Private client, employer, health, account or analytics data, API keys, tokens or passwords. This repo is public.
