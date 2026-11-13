# Changelog

All notable updates to this library are recorded here.

## [0.22.0] - 2026-11-13

### Added

- Design-15 Motion Prompt: guide to showheyohtaki/motion-prompt (MIT, commit da14d9c). A numbered gallery of named motion-graphics moves, camera moves and transitions, UI parts, landing-page effects, photo looks and art styles, each with a live sample; the skill opens it as a picker and rebuilds your picks in the project.

## [0.21.0] - 2026-11-11

### Added

- New Tool Library category: Music / 音樂.
- Music-01 Suno Lyric Weaver: rhymed, hook-first Suno lyrics with section tags, built for Mandarin.
- Music-02 Suno Style Prompt: Suno Style prompt with genre blend, groove, instruments, vocal, mood, exclusions and A/B variants.

## [0.20.0] - 2026-11-08

### Added

- Design-14 unslop: guide to heydamir/unslop by Damir Sokolovsky (CC BY 4.0, commit 1d13095). Audits a vibecoded, AI-looking screen, sets a product-specific direction, then redesigns it in nine ordered passes; optional live-site snapshot and before-and-after story video.

## [0.19.1] - 2026-11-07

### Changed

- Content-01 instagram-agent-skill: install steps for the Claude app (upload in Settings, no Terminal) now come first.

## [0.19.0] - 2026-11-07

### Added

- New Tool Library category Content & Social (內容與社群), IDs Content-NN, for tools that plan and write social posts.
- Content-01 instagram-agent-skill: guide to GoldenSharkStudio/instagram-agent-skill (MIT, commit 6a28b3b), fourteen ig-* skills covering Reel hooks and scripts, captions, carousels, stories, comments, replies, DMs, profile, weekly plan, repurposing and audits. English and Brazilian Portuguese only.

## [0.18.0] - 2026-11-04

### Added

- UI-42 Neumorphic Controls (新擬態元件六式), Inputs & Controls: six soft-UI controls on one surface — light switch, thermostat dial, media player, file upload, booking picker and quantity stepper — each with press-sink-and-spring-back feedback, contrast rules, keyboard support and reduced-motion handling. Skill recipe with bilingual prompt terms, plus demo page `demo/ui-42-neumorphic-controls.html`.

## [0.17.1] - 2026-11-02

### Fixed

- Removed the last character names from skill text: Video-03 now points to Video-01 HyperFrames Video and Video-04 Remotion Shotcraft by ID and real name, and Design-07 says "this library" instead of "this crew".

## [0.17.0] - 2026-11-02

### Added

- UI-41 ASCII Sharks (ASCII 鯊魚海洋), Ambient & Attention: a living ASCII ocean of fish schools and hunting sharks behind a hero, built on stackedlol/ascii-sharks (MIT, commit a0074c1). Skill recipe plus demo page `demo/ui-41-ascii-sharks.html`; the engine is bundled unchanged with its MIT notice in `demo/assets/vendor/ascii-sharks.min.js`.

## [0.16.1] - 2026-11-01

### Removed

- "Inspired by" credits to video creators on UI-15 to UI-22, UI-23 and UI-25 to UI-40, and the Credit sections added to Design-12, Video-01 and Video-05, because the original creators could not be confirmed. Tool guides keep their links to each tool's own GitHub page. Video-04 keeps its Remotion licence note.

## [0.16.0] - 2026-11-01

The whole collection is now the **Skill Library**, and every category numbers its own skills from 01.

### Changed

- New IDs, one sequence per category: UI-01 to UI-40, Design-01 to Design-13, Dev-01 to Dev-06, Video-01 to Video-05, Learning-01. Folders and demo pages are renamed to match (for example `skills/ui-07-drag-to-expand-and-collapse/`, `skills/design-13-quality-pack/`). Old numbers map in the original order: UI follows 01–14, 22–30, 43, 45–60; Design follows workflow order.
- The section of tools inside is now the **Tool Library** (Design, Dev & Workflow, Video & Media), so it no longer shares a name with the whole Skill Library.
- README has "Next numbers" per category and a Credits section. AGENTS.md now tells agents to report the section, category and ID before adding anything new, and to credit every source.

### Added

- `## Credit` sections on every skill that came from someone else: the layout interactions UI-15 to UI-22 (叨叨AI是我), the sixteen motion effects UI-25 to UI-40 (大锤和AI), and Design-12, Video-01, Video-04 and Video-05 (tools they build on). Video-04 notes Remotion's company-licence rule.

## [0.15.0] - 2026-11-01

The repo is now Lilian O.'s whole Library: one index with a UI Library, a Skill Library and a Learning Library. Character names are gone; every tool skill uses its real name. Skill numbers don't change.

### Changed

- README is now the Library index: 1. UI Library (01–14, 22–30, 43, 45–60), 2. Skill Library (Design, Dev & Workflow, Video & Media), 3. Learning Library, 4. References.
- Guide skills renamed to their tool names, folders included: design-01-wireframer, design-02-drawio, design-03-taste-pack, design-05-ui-ux-pro-max-uizze, design-06-shadcn-ui, design-07-huashu-baoyu-open-design, design-13-quality-pack, design-04-awesome-design-md, design-08-gsap-skills, design-09-pencilplaybook, design-10-landing-page-generator, design-11-motionsites, dev-01-find-skills, dev-02-grill-me, dev-03-codebase-architecture, dev-04-tdd, dev-05-agent-browser, video-02-hyperframes, dev-06-reddit-automation, video-03-openfilm.
- 41 HyperFrames and 44 OpenFilm moved to the new Video & Media category.
- AGENTS.md rewritten so any agent (Claude, Codex) reads the Library index first; CLAUDE.md points to it. CONTRIBUTING and the guide template drop character naming.

### Added

- 61 cangjie-skill (Learning Library): distil a book, course or transcript into tested, reusable skills.
- Lilian's own tested skills, previously only installed on her Claude account: 62 HyperFrames Video, 63 Remotion Shotcraft (Video & Media), 64 Framer (Design), 65 Sena & Pudding Reel Builder (Video & Media).
- MIT licence for Lilian O.'s own work; replaces LICENSE-DECISION.md.

## [0.14.0] - 2026-11-01

The library is now sorted onto four shelves with eleven categories, and every skill sits in exactly one. Skill numbers don't change.

### Changed

- New catalogue structure in the README, CONTRIBUTING, the skill template and the demo gallery (filters by shelf):
  - 版面 / Layout: 導覽與視圖 Navigation & Views (01, 07, 27, 30, 43) · 網格與面板 Grids & Panels (06, 24, 25, 26, 29)
  - 元件 / Components: 輸入與控制 Inputs & Controls (02, 03, 05, 28) · 回饋與載入 Feedback & Loading (04, 08, 60)
  - 動效 / Motion: 動效基礎 Motion Foundations (45–47) · 滾動動效 Scroll (10, 12, 48–50) · 游標與懸停 Cursor & Hover (09, 13, 14, 51–54) · 文字動效 Text & Type (22, 23, 55–57) · 氛圍與吸睛 Ambient & Attention (11, 58, 59)
  - 工具組 / Toolkits: 設計工具組 Design Toolkit · 開發與工作流工具組 Dev & Workflow Toolkit (unchanged)
- Every existing skill's `**Category:**` line updated to its new category. The old categories 動態視覺效果 Motion Effects and 排版互動 Layout Relationships are retired; their skills moved into the categories above.
- The single 45 16 Essential Motion Effects skill is split into sixteen skills, one per effect, each with its own demo page: 45 Easing & Timing (the base timing rules every motion skill uses), 46 Spring, 47 Stagger, 48 Scroll Storytelling, 49 Parallax, 50 Scroll Reveal, 51 Spotlight, 52 Tilt, 53 Magnetic, 54 Hover Lift, 55 Scramble Text, 56 Typewriter, 57 Count Up, 58 Border Beam, 59 Marquee, 60 Shimmer.
- `demo/45-motion-essentials.html` becomes `demo/motion-essentials.html`, a showcase of 45–60 grouped by category; each single demo page links to the rest of its category. Demo chain: 43 → 45 … 60 → 30.
- Next number is 61.

## [0.13.0] - 2026-11-01

### Added

- 45 16 Essential Motion Effects (常用動效十六式): a named vocabulary of the sixteen motion effects found on most product pages (Border Beam, Spotlight, Tilt, Scroll Storytelling, Scramble Text, Parallax, Magnetic, Typewriter, Marquee, Shimmer, Count Up, Scroll Reveal, Spring, Stagger, Hover Lift, Easing), each with its job, key spec, technique, reduced-motion fallback and prompt line in English and Chinese, plus a timing and easing cheat sheet. Concept inspired by 大锤和AI's Douyin video on 16 common animation effects; all text and demos written for this library. Demo at `demo/45-motion-essentials.html`: all sixteen live on one page with a reduced-motion preview switch, linked between 43 and 30.

## [0.12.0] - 2026-10-31

### Added

- 44 Studio Otter (水獺片場師): guide to OpenFilm's openfilm skill (MIT), the open-source AI video agent where a coding agent writes a film as web pages and Studio, a local editor, lets you change it by hand. Routes to its built-in film styles and its look/render/get commands, notes the overlap with 41 Reel Raccoon, Flip Fox and Director Crane, and the OpenFilm trademark terms. Written in our own words; nothing copied.

## [0.11.0] - 2026-10-31

### Added

- 43 Card-to-Hero Carousel (卡片展開輪播): a full-bleed hero with a queue of portrait cards; tapping a card grows it from its exact spot into the new background, the copy swaps with a stagger and the queue slides along with FLIP. Next grows, previous crossfades when its card is off screen, rapid taps stack, swipe and arrow keys work, live-region announcements, crossfade under reduced motion. Dependency-free reference demo at `demo/ui-24-card-to-hero-carousel.html` with original generated scenes, linked between 14 and 30.

## [0.10.1] - 2026-10-31

### Added

- 14 Cursor-driven Animated Hero (游標驅動的動態主視覺): layered parallax hero with a spotlight that reveals a second layer; touch drift and drag, keyboard focus moves the spotlight, static under reduced motion. Fills the number that had been reserved, so 01–42 now run without gaps. Demo at `demo/ui-14-cursor-driven-hero.html`, linked between 13 and 30.

## [0.10.0] - 2026-10-31

Reviewed the skills.sh install top 10 (dated 2026-10-29) against their real repos. All guides are written in our own words; none of the original text is copied. No skill appeared twice, but three groups overlap, so ten skills became seven crew members.

### Added

- New category 開發與工作流工具組 / Dev & Workflow Toolkit.
- 36 Truffle Pig (松露豬尋寶師): guide to Vercel's find-skills (MIT).
- 37 Grill Badger (獾式追問師): guide to Matt Pocock's grill-me and grill-with-docs (MIT), merged because both run the same interview.
- 38 Weaver Bird (織巢鳥架構師): guide to Matt Pocock's improve-codebase-architecture (MIT).
- 39 Test Tortoise (烏龜測試師): guide to Matt Pocock's tdd (MIT).
- 40 Ferret Fetcher (雪貂操作員): guide to Vercel's agent-browser (Apache-2.0).
- 41 Reel Raccoon (浣熊剪片師): guide to HeyGen's hyperframes, hyperframes-cli and media-use (Apache-2.0), merged as one tool family; notes the overlap with Flip Fox (HyperFrames).
- 42 Meerkat Lookout (狐獴瞭望員): guide to doany.ai's reddit-automation (MIT).

## [0.9.0] - 2026-10-31

### Added

- 35 Glow Firefly (螢火蟲大片師): guide to MotionSites' motionsites-web-builder (instructions and scripts MIT; examples and media © MotionSites) for cinematic heroes and landing pages with a screenshot-and-fix loop. Links to the original only; none of its examples or media are copied.

### Fixed

- README Design Toolkit table: rows 31–33 were missing their skill links and row 34 linked to skill 31.

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
- `demo/ui-23-dashboard-nav-patterns.html`: one mini dashboard that switches between all six patterns, with a moving active pill, keyboard and long-press tooltips, in-place quick actions, a bottom-bar layout under 560px and a reduced-motion fallback.

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
