# Changelog

All notable updates to this library are recorded here.

## [0.4.0] - 2026-10-21

### Added

- New category 排版互動 / Layout Relationships: eight interactions where layout pieces respond to each other, inspired by a short video on premium layout interactions for vibe coding (叨叨AI是我). Written in our own words with full interaction contracts.
  - 22 Knockout Title: photo shows through giant type; scroll zooms it to full bleed and back.
  - 23 Inline Image Title: a text-height image inside a headline expands in place.
  - 24 Expanding Grid: one card spans the row while the rest reflow below.
  - 25 Offset Columns: two columns scroll at different speeds and land aligned.
  - 26 Sticky Date Rail: oversized dates stick and push each other out.
  - 27 Folder Tabs: stacked folders, the chosen one comes to the front.
  - 28 Bubble Picker: packed circles that grow and push neighbours when selected.
  - 29 Split View: draggable divider with content re-layout and three snap points.

## [0.3.1] - 2026-10-20

### Changed

- 17 Pearl Peacock (Taste Pack) now covers the whole Taste Skill family after its 2026-10-19 reorganisation: the default `design-taste-frontend` (including app screens and restyles), the dial-based classics in Leonxlnx/taste-skill-classics, and the reference-board skills in Leonxlnx/imagegen-skills (`imagegen-frontend-web`, `imagegen-frontend-mobile`, `brandkit`, `image-to-code`).

### Fixed

- Install commands for `high-end-visual-design` and `minimalist-ui` pointed at the old repo; they now use Leonxlnx/taste-skill-classics.

## [0.3.0] - 2026-10-18

### Added

- New category 設計工具組 / Design Toolkit: seven character guides that route to 15 open-source design skills, numbered in workflow order.
  - 15 Sketch Squirrel (Wireframer): agilek/wireframer-skill.
  - 16 Blueprint Beaver (draw.io): Agents365-ai/drawio-skill.
  - 17 Pearl Peacock (Taste Pack): anthropics frontend-design; Leonxlnx design-taste-frontend, high-end-visual-design, minimalist-ui.
  - 18 Magpie Muse (UI UX Pro Max + UIZZE): nextlevelbuilder ui-ux-pro-max; UIZZE anti-ui-slop.
  - 19 Builder Ant (shadcn/ui): shadcn.
  - 20 Octo Studio (Huashu + Baoyu): alchaincyf huashu-design; JimLiu baoyu-design.
  - 21 Hawk Inspector (Quality Pack): Vercel web-design-guidelines; educlopez ui-craft; pbakaus impeccable; Emil Kowalski emil-design-eng.
- `templates/TOOLKIT-SKILL-TEMPLATE.md` and contribution rules for crew members (licence check, own words, one job each).

### Notes

- Number 14 stays reserved for the planned cursor-driven hero.

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
