# Changelog

All notable updates to this library are recorded here.

## [0.2.0] - 2026-10-15

### Changed

- Reorganised the whole library as skills: every entry is now `skills/<NN>-<name>/SKILL.md`, usable by Claude Code and Codex.
- Patterns 01–08 moved from `patterns/` into `skills/` with frontmatter, a category and their original copy-ready prompts. The `patterns/` folder was removed so nothing is kept twice.
- Motion skills renumbered 09–13 and given Chinese names and categories.
- README is now a catalogue grouped into four categories, with install instructions for Claude Code and Codex.
- CONTRIBUTING describes how to add a skill and pick a category.

### Added

- Pattern files 02–08. The index listed these in 0.1.0, but only pattern 01 had been committed.
- Five motion skill specifications: cursor-luminous-flow, scroll-helix-flow, immersive-float, scroll-vortex-transit and hover-door-bloom.
- `templates/SKILL-TEMPLATE.md` for new skills.

### Planned

- 14 — Cursor-driven animated hero / 游標驅動的動態主視覺 (previously reserved as 09; not yet documented).

## [0.1.0] - 2026-09-29

### Added

- Repository foundation and maintenance guidance.
- Patterns 01–08 with bilingual names, effect summaries, and copy-ready English prompts.
