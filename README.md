# UI Interaction Library

A growing library of reusable UI interactions and motion effects, maintained by Lilian O. Every entry is a self-contained skill: a `SKILL.md` that describes the interaction, its accessibility and fallback rules, and a copy-ready prompt. AI coding tools such as Claude Code and Codex can use the skills directly, and designers and developers can read them as a reference.

Each skill is an implementation recipe, not finished code. It tells you, or an AI tool, how to build the interaction well.

## Catalogue / 目錄

### 版面與導覽 / Layout & Navigation

| No. | 中文 | English | Skill |
| --- | --- | --- | --- |
| 01 | 共享元素展開 | Shared Element Expansion | [`01-shared-element-expansion`](skills/01-shared-element-expansion/SKILL.md) |
| 06 | 拖曳排序 | Drag to Reorder | [`06-drag-to-reorder`](skills/06-drag-to-reorder/SKILL.md) |
| 07 | 拖曳展開與收合 | Drag to Expand & Collapse | [`07-drag-to-expand-and-collapse`](skills/07-drag-to-expand-and-collapse/SKILL.md) |
| 30 | 後台菜單六式 | Dashboard Nav Patterns (Transparent Nav · Right Rail · Expanding Tab · Title as Nav · Icon Rail · Quick Actions) | [`30-dashboard-nav-patterns`](skills/30-dashboard-nav-patterns/SKILL.md) |

### 輸入與控制 / Input & Controls

| No. | 中文 | English | Skill |
| --- | --- | --- | --- |
| 02 | 彈性數值調節 | Elastic Value Adjustment | [`02-elastic-value-adjustment`](skills/02-elastic-value-adjustment/SKILL.md) |
| 03 | 滑動選擇 | Swipe Selection | [`03-swipe-selection`](skills/03-swipe-selection/SKILL.md) |
| 05 | 浮動標籤 | Floating Label | [`05-floating-label`](skills/05-floating-label/SKILL.md) |

### 回饋與狀態 / Feedback & State

| No. | 中文 | English | Skill |
| --- | --- | --- | --- |
| 04 | 動態狀態切換 | Animated State Transition | [`04-animated-state-transition`](skills/04-animated-state-transition/SKILL.md) |
| 08 | 飛向目標的回饋 | Fly-to-Target Feedback | [`08-fly-to-target-feedback`](skills/08-fly-to-target-feedback/SKILL.md) |

### 動態視覺效果 / Motion Effects

| No. | 中文 | English | Trigger | Skill |
| --- | --- | --- | --- | --- |
| 09 | 游標流光 | Cursor-driven Luminous Flow | Cursor | [`09-cursor-luminous-flow`](skills/09-cursor-luminous-flow/SKILL.md) |
| 10 | 滾動螺旋流動 | Scroll-driven Helix Flow | Scroll | [`10-scroll-helix-flow`](skills/10-scroll-helix-flow/SKILL.md) |
| 11 | 沉浸式漂浮 | Immersive Float | Click / tap | [`11-immersive-float`](skills/11-immersive-float/SKILL.md) |
| 12 | 滾動漩渦轉場 | Scroll-driven Vortex Transit | Scroll | [`12-scroll-vortex-transit`](skills/12-scroll-vortex-transit/SKILL.md) |
| 13 | 滑過開門綻放 | Hover-triggered Door Bloom | Hover / focus | [`13-hover-door-bloom`](skills/13-hover-door-bloom/SKILL.md) |
| 14 | 游標驅動的動態主視覺 | Cursor-driven Animated Hero | Cursor / drag | [`14-cursor-driven-hero`](skills/14-cursor-driven-hero/SKILL.md) |
| 43 | 卡片展開輪播 | Card-to-Hero Carousel | Click / tap / swipe | [`43-card-to-hero-carousel`](skills/43-card-to-hero-carousel/SKILL.md) |
| 45 | 常用動效十六式 | 16 Essential Motion Effects (Border Beam · Spotlight · Tilt · Scroll Storytelling · Scramble Text · Parallax · Magnetic · Typewriter · Marquee · Shimmer · Count Up · Scroll Reveal · Spring · Stagger · Hover Lift · Easing) | Mixed | [`45-motion-essentials`](skills/45-motion-essentials/SKILL.md) |

### 排版互動 / Layout Relationships

Eight interactions where pieces of a layout respond to each other: type opens onto images, cards make room, columns drift and panels trade space. Design the layout relationship first, then let the interaction move it.

| No. | 中文 | English | Trigger | Skill |
| --- | --- | --- | --- | --- |
| 22 | 鏤空大標題 | Knockout Title | Scroll | [`22-knockout-title`](skills/22-knockout-title/SKILL.md) |
| 23 | 標題嵌小圖 | Inline Image Title | Tap / click | [`23-inline-image-title`](skills/23-inline-image-title/SKILL.md) |
| 24 | 點一格撐成通欄 | Expanding Grid | Tap / click | [`24-expanding-grid`](skills/24-expanding-grid/SKILL.md) |
| 25 | 兩列錯速滾動 | Offset Columns | Scroll | [`25-offset-columns`](skills/25-offset-columns/SKILL.md) |
| 26 | 左欄日期吸頂 | Sticky Date Rail | Scroll | [`26-sticky-date-rail`](skills/26-sticky-date-rail/SKILL.md) |
| 27 | 檔案夾標籤頁 | Folder Tabs | Tap / keyboard | [`27-folder-tabs`](skills/27-folder-tabs/SKILL.md) |
| 28 | 圓泡堆疊選擇 | Bubble Picker | Tap / keyboard | [`28-bubble-picker`](skills/28-bubble-picker/SKILL.md) |
| 29 | 拖動分屏比例 | Split View | Drag / keyboard | [`29-split-view`](skills/29-split-view/SKILL.md) |

### 設計工具組 / Design Toolkit

A crew of characters, each one a guide to the best open-source design skills for one job. Numbered in workflow order: sketch the flow, map the system, set the taste, gather references, build, produce, then inspect. Later additions take the next free number; 31 sits between taste and references in the workflow. Each crew member explains when to call the original skills and how to install them; it does not copy them.

| No. | 中文 | English (powered by) | Job | Skill |
| --- | --- | --- | --- | --- |
| 15 | 松鼠草圖師 | Sketch Squirrel (Wireframer) | Lo-fi clickable wireframes | [`15-sketch-squirrel-wireframer`](skills/15-sketch-squirrel-wireframer/SKILL.md) |
| 16 | 河狸藍圖師 | Blueprint Beaver (draw.io) | Editable system and flow diagrams | [`16-blueprint-beaver-drawio`](skills/16-blueprint-beaver-drawio/SKILL.md) |
| 17 | 孔雀品味師 | Pearl Peacock (Taste Pack + Hallmark + Cinematic UI) | Visual direction for web and app UI without AI slop; strict anti-AI-look rules; film-directed pages; restyles; reference boards | [`17-pearl-peacock-taste-pack`](skills/17-pearl-peacock-taste-pack/SKILL.md) |
| 18 | 喜鵲靈感庫 | Magpie Muse (UI UX Pro Max + UIZZE) | Palettes, fonts and real-screen references | [`18-magpie-muse-ui-references`](skills/18-magpie-muse-ui-references/SKILL.md) |
| 19 | 螞蟻組件師 | Builder Ant (shadcn/ui) | Build with React components | [`19-builder-ant-shadcn`](skills/19-builder-ant-shadcn/SKILL.md) |
| 20 | 章魚工作室 | Octo Studio (Huashu + Baoyu + Open Design) | Prototypes, decks and animations in one prompt; a full local design workspace | [`20-octo-studio-huashu-baoyu`](skills/20-octo-studio-huashu-baoyu/SKILL.md) |
| 21 | 鷹眼質檢員 | Hawk Inspector (Quality Pack) | Standards, score, polish and motion check | [`21-hawk-inspector-quality-pack`](skills/21-hawk-inspector-quality-pack/SKILL.md) |
| 31 | 變色龍換裝師 | Costume Chameleon (Awesome DESIGN.md + design-md-chrome) | Borrow a proven brand's design system as a DESIGN.md, or extract one from any site, then make it your own | [`31-costume-chameleon-awesome-design-md`](skills/31-costume-chameleon-awesome-design-md/SKILL.md) |
| 32 | 燕子動效師 | Swift Swallow (GSAP Skills) | Scroll animation and timeline choreography in code | [`32-swift-swallow-gsap`](skills/32-swift-swallow-gsap/SKILL.md) |
| 33 | 鵜鶘畫板師 | Canvas Pelican (PencilPlaybook) | Token-consistent screens on a Pencil.dev canvas | [`33-canvas-pelican-pencilplaybook`](skills/33-canvas-pelican-pencilplaybook/SKILL.md) |
| 34 | 蜜蜂轉化師 | Buzz Bee (Landing Page Generator) | Landing page copy and structure that converts | [`34-buzz-bee-landing-page-generator`](skills/34-buzz-bee-landing-page-generator/SKILL.md) |
| 35 | 螢火蟲大片師 | Glow Firefly (MotionSites Web Builder) | Cinematic heroes and landing pages with real video and a screenshot-and-fix loop; prompts for Lovable, Bolt and v0 | [`35-glow-firefly-motionsites`](skills/35-glow-firefly-motionsites/SKILL.md) |

### 開發與工作流工具組 / Dev & Workflow Toolkit

The same crew idea for building, testing and shipping: plan the work, shape the code, test it, drive a browser, make video, and find an audience. Picked from the skills.sh install top 10 of 2026-10-29; overlapping skills share one crew member, so ten skills become seven characters; 44 was added later. Each one credits and installs the originals; none are copied.

| No. | 中文 | English (powered by) | Job | Skill |
| --- | --- | --- | --- | --- |
| 36 | 松露豬尋寶師 | Truffle Pig (Find Skills) | Find an existing skill before building one | [`36-truffle-pig-find-skills`](skills/36-truffle-pig-find-skills/SKILL.md) |
| 37 | 獾式追問師 | Grill Badger (Grill Me + Grill with Docs) | Be questioned hard until a plan has no soft spots; optional glossary and decision records | [`37-grill-badger-grill-me`](skills/37-grill-badger-grill-me/SKILL.md) |
| 38 | 織巢鳥架構師 | Weaver Bird (Codebase Architecture) | Refactoring opportunities as a visual report | [`38-weaver-bird-codebase-architecture`](skills/38-weaver-bird-codebase-architecture/SKILL.md) |
| 39 | 烏龜測試師 | Test Tortoise (TDD) | Build and fix test-first | [`39-test-tortoise-tdd`](skills/39-test-tortoise-tdd/SKILL.md) |
| 40 | 雪貂操作員 | Ferret Fetcher (agent-browser) | Drive a real browser from a coding agent | [`40-ferret-fetcher-agent-browser`](skills/40-ferret-fetcher-agent-browser/SKILL.md) |
| 41 | 浣熊剪片師 | Reel Raccoon (HyperFrames Pack) | Video from web code, plus music, images and voiceover | [`41-reel-raccoon-hyperframes`](skills/41-reel-raccoon-hyperframes/SKILL.md) |
| 42 | 狐獴瞭望員 | Meerkat Lookout (Reddit Automation) | Find real demand on Reddit and draft honest, disclosed replies | [`42-meerkat-lookout-reddit`](skills/42-meerkat-lookout-reddit/SKILL.md) |
| 44 | 水獺片場師 | Studio Otter (OpenFilm) | Agent-made films you finish by hand in a real editor; ten built-in film styles; NLE export | [`44-studio-otter-openfilm`](skills/44-studio-otter-openfilm/SKILL.md) |

Next number: **46**. Numbers 01–45 are all in use.

## Live demo

Every interaction skill has a working demo in `demo/`. `demo/index.html` is the gallery; each skill has its own page named like its folder (for example `demo/07-drag-to-expand-and-collapse.html`), and skills 22–29 are shown together on `demo/returns-bench.html`. Deploy the repo on Vercel to browse them at a live link: `vercel.json` sends the site root to the gallery. Design Toolkit (15–21, 31–35) and Dev & Workflow Toolkit (36–42, 44) skills are guides, so they have no interaction demo; `demo/design-toolkit.html` is a visual field guide to the ten design skills they cover, showing which crew member carries each one.

## How to use

**With Claude Code:** copy the skill folders you want into your project's `.claude/skills/` folder (or `~/.claude/skills/` to use them in every project).

**With Codex:** copy them into your project's `.agents/skills/` folder (or `~/.agents/skills/`).

**Without installing:** point the AI tool at this repository and name the skill, for example "Use skill 07 from LillianOu/ui-interaction-library to build a bottom sheet."

**By hand:** open a `SKILL.md` and paste its copy-ready prompt into any AI coding tool.

**Design and Dev & Workflow crews (15–21, 31–42, 44):** install the crew member as above, then install the originals it names with the commands in its `SKILL.md` (31 installs a `DESIGN.md` file into your project rather than a skill). Call a character by name, for example "Ask Hawk Inspector to check this page."

## Repository layout

```
skills/<NN>-<name>/SKILL.md   one folder per skill, numbered in the order added
templates/SKILL-TEMPLATE.md   starting point for a new interaction skill
templates/TOOLKIT-SKILL-TEMPLATE.md   starting point for a new Design Toolkit crew member
CONTRIBUTING.md               how to add a skill and pick its category
CHANGELOG.md                  what changed and when
demo/                         live demos: index.html gallery, one page per skill, shared assets/demo.css, _template.html
vercel.json                   Vercel config (root redirects to /demo/)
LICENSE-DECISION.md           licence status
```

## Working principles

- Describe reusable behaviours, not a single product scenario.
- Include pointer, touch, keyboard, accessibility, reduced-motion, cancellation, state, and implementation safeguards where relevant.
- Keep every skill self-contained, so it still works when copied on its own.
- Do not describe unfinished work as production-complete.

## Licence

No licence has been chosen yet. See [LICENSE-DECISION.md](LICENSE-DECISION.md).

## Game UI References / 遊戲 UI 參考

Curated game UI reference sites and licence-cleared asset sources: [`game-ui-references.md`](game-ui-references.md). Downloaded assets go in [`game-assets/`](game-assets/README.md).
