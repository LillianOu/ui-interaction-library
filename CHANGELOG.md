# Changelog

All notable updates to this library are recorded here.

## [0.8.0] - 2026-10-29

Reviewed the ten skills in 庫米工具's "UI 設計 10 大 skill 榜" post against their real repos. All guides are written in our own words; none of the original text is copied.

### Added

- 32 Swift Swallow (燕子動效師): guide to GreenSock's official gsap-skills (MIT) for scroll animation and timelines.
- 33 Canvas Pelican (鵜鶘畫板師): guide to stevembarclay's PencilPlaybook (MIT) for designing on a Pencil.dev canvas.
- 34 Buzz Bee (蜜蜂轉化師): guide to alirezarezvani's landing-page-generator (MIT) for conversion copy and structure.
- `demo/design-toolkit.html`: a visual field guide to all ten skills, with a drawing of what each produces, the crew member that carries it and its install line.

### Changed

- 17 Pearl Peacock now routes to Hallmark (Nutlope/hallmark, MIT) for strict anti-AI-look rules and Cinematic UI (akseolabs-seo/cinematic-ui, MIT) for film-directed pages.
- 20 Octo Studio now routes to Open Design (nexu-io/open-design, Apache-2.0), a local design workspace app with an MCP server, and explains why the community "Claude Design Skill" is not wrapped.
- 31 Costume Chameleon now routes to design-md-chrome (bergside/design-md-chrome, MIT), a Chrome extension that extracts a DESIGN.md from any site.
- UI/UX Pro Max and Taste Skill were already covered by 18 Magpie Muse and 17 Pearl Peacock.

### Not added

- jiji262/claude-design-skill: its README states the content is Anthropic's Claude Design system prompt, so it does not meet the open-licence rule. Use Claude Design in the Claude app.

## [0.7.0] - 2026-10-25

### Added

- 31 Costume Chameleon (變色龍換裝師), in Design Toolkit: a guide to VoltAgent's awesome-design-md (MIT), a collection of 84 brand-inspired DESIGN.md design-system files. Routes by the feeling you want to a costume, installs it as one file in the project root, lints it with Google's `@google/design.md`, and covers making it your own (fonts, colours, trademarks). Written in our own words; none of the original files are copied.

## [0.6.0] - 2026-10-22

### Added

- 30 Dashboard Nav Patterns (後台菜單六式), in Layout & Navigation: six named dashboard menu patterns — Transparent Nav, Right Rail, Expanding Tab, Title as Nav, Icon Rail + Tooltip and Quick Actions — each with a key spec, interaction contract, and English and Chinese prompt terms. Inspired by a short video on premium dashboard menus (我叫-西瓜同学), written in our own words.
- `demo/30-dashboard-nav-patterns.html`: one mini dashboard that switches between all six patterns, with a moving active pill, keyboard and long-press tooltips, in-place quick actions, a bottom-bar layout under 560px and a reduced-motion fallback.

## [0.5.0] - 2026-10-22

### Added

- Live demo for every interaction skill: `demo/01-…` to `demo/13-…` pages, one per skill, each built on the shared shell `demo/assets/demo.css` with its own inline, dependency-free interaction code, reduced-motion fallback and keyboard support.
- `demo/index.html` is now a gallery of all interaction skills, filterable by category; skills 22–29 link to their sections on `demo/returns-bench.html`.
- `demo/_template.html` and a CONTRIBUTING step: every new interaction skill ships with a demo page.

### Changed

- The Returns Bench showcase moved from `demo/index.html` to `demo/returns-bench.html`; `vercel.json` now opens the gallery.

## [0.4.1] - 2026-10-22

### Added

- `demo/index.html`: one live page demonstrating skills 22–29, each section labelled with its skill number and linked to its `SKILL.md`.
- `vercel.json` so the repo can be deployed on Vercel with the demo at the site root.

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
