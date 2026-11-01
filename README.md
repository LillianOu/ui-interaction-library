# Lilian O. — Skill Library

Every skill Lilian O. uses, in one place, sorted by category. Each entry is a self-contained `SKILL.md` that people can read and AI tools (Claude, Claude Code, Codex, Cursor) can use directly.

**For AI agents:** read this page first, then open the `SKILL.md` of the entry you need. Agent rules are in [`AGENTS.md`](AGENTS.md).

```
Skill Library
├── 1. UI Library        effects you put into pages and apps       UI-01 … UI-41
├── 2. Tool Library      tools you use to make things
│   ├── Design                                                      Design-01 … Design-13
│   ├── Dev & Workflow                                              Dev-01 … Dev-06
│   └── Video & Media                                               Video-01 … Video-05
├── 3. Learning Library  learning from books, courses and talks     Learning-01
└── 4. References        links to check, not skills
```

Each category numbers its own skills from 01, and a new skill takes the next number in its category. Folders are named after the ID (for example `skills/design-01-wireframer/`) and sit flat in `skills/` so AI tools can find them. Tools keep their real names.

## 1. UI Library / UI 介面庫

Reusable interactions and motion effects. Each is an implementation recipe with accessibility and fallback rules and a copy-ready prompt, not finished code. Every one has a live demo (see [Live demo](#live-demo)).

| Shelf | Categories |
| --- | --- |
| 版面 / Layout | 導覽與視圖 Navigation & Views (5) · 網格與面板 Grids & Panels (5) |
| 元件 / Components | 輸入與控制 Inputs & Controls (4) · 回饋與載入 Feedback & Loading (3) |
| 動效 / Motion | 動效基礎 Motion Foundations (3) · 滾動動效 Scroll (5) · 游標與懸停 Cursor & Hover (7) · 文字動效 Text & Type (5) · 氛圍與吸睛 Ambient & Attention (4) |

### 版面 / Layout

How the page is arranged and how you move around it.

#### 導覽與視圖 / Navigation & Views

Moving between views and pages: expanding cards, sheets, tabs, menus, carousels.

| No. | 中文 | English | Trigger | Skill |
| --- | --- | --- | --- | --- |
| UI-01 | 共享元素展開 | Shared Element Expansion | Tap | [`ui-01-shared-element-expansion`](skills/ui-01-shared-element-expansion/SKILL.md) |
| UI-07 | 拖曳展開與收合 | Drag to Expand & Collapse | Drag | [`ui-07-drag-to-expand-and-collapse`](skills/ui-07-drag-to-expand-and-collapse/SKILL.md) |
| UI-20 | 檔案夾標籤頁 | Folder Tabs | Tap / keyboard | [`ui-20-folder-tabs`](skills/ui-20-folder-tabs/SKILL.md) |
| UI-23 | 後台菜單六式 | Dashboard Nav Patterns (Transparent Nav · Right Rail · Expanding Tab · Title as Nav · Icon Rail · Quick Actions) | Tap / keyboard | [`ui-23-dashboard-nav-patterns`](skills/ui-23-dashboard-nav-patterns/SKILL.md) |
| UI-24 | 卡片展開輪播 | Card-to-Hero Carousel | Click / tap / swipe | [`ui-24-card-to-hero-carousel`](skills/ui-24-card-to-hero-carousel/SKILL.md) |

#### 網格與面板 / Grids & Panels

Arranging and rearranging content: reorderable lists, reflowing grids, columns, rails, resizable splits.

| No. | 中文 | English | Trigger | Skill |
| --- | --- | --- | --- | --- |
| UI-06 | 拖曳排序 | Drag to Reorder | Drag | [`ui-06-drag-to-reorder`](skills/ui-06-drag-to-reorder/SKILL.md) |
| UI-17 | 點一格撐成通欄 | Expanding Grid | Tap / click | [`ui-17-expanding-grid`](skills/ui-17-expanding-grid/SKILL.md) |
| UI-18 | 兩列錯速滾動 | Offset Columns | Scroll | [`ui-18-offset-columns`](skills/ui-18-offset-columns/SKILL.md) |
| UI-19 | 左欄日期吸頂 | Sticky Date Rail | Scroll | [`ui-19-sticky-date-rail`](skills/ui-19-sticky-date-rail/SKILL.md) |
| UI-22 | 拖動分屏比例 | Split View | Drag / keyboard | [`ui-22-split-view`](skills/ui-22-split-view/SKILL.md) |

### 元件 / Components

Things people touch, and what they get back.

#### 輸入與控制 / Inputs & Controls

Entering or choosing a value: fields, pickers, sliders, steppers, swipes.

| No. | 中文 | English | Trigger | Skill |
| --- | --- | --- | --- | --- |
| UI-02 | 彈性數值調節 | Elastic Value Adjustment | Drag | [`ui-02-elastic-value-adjustment`](skills/ui-02-elastic-value-adjustment/SKILL.md) |
| UI-03 | 滑動選擇 | Swipe Selection | Swipe | [`ui-03-swipe-selection`](skills/ui-03-swipe-selection/SKILL.md) |
| UI-05 | 浮動標籤 | Floating Label | Type | [`ui-05-floating-label`](skills/ui-05-floating-label/SKILL.md) |
| UI-21 | 圓泡堆疊選擇 | Bubble Picker | Tap / keyboard | [`ui-21-bubble-picker`](skills/ui-21-bubble-picker/SKILL.md) |

#### 回饋與載入 / Feedback & Loading

Confirming actions and showing loading, success, error or progress.

| No. | 中文 | English | Trigger | Skill |
| --- | --- | --- | --- | --- |
| UI-04 | 動態狀態切換 | Animated State Transition | Tap | [`ui-04-animated-state-transition`](skills/ui-04-animated-state-transition/SKILL.md) |
| UI-08 | 飛向目標的回饋 | Fly-to-Target Feedback | Tap | [`ui-08-fly-to-target-feedback`](skills/ui-08-fly-to-target-feedback/SKILL.md) |
| UI-40 | 流光 | Shimmer | Loading / ambient | [`ui-40-shimmer`](skills/ui-40-shimmer/SKILL.md) |

### 動效 / Motion

Motion grouped by what triggers it. Start with Motion Foundations: its timing rules apply to every other entry.

#### 動效基礎 / Motion Foundations

The rules behind all motion: easing, duration, spring physics, stagger.

| No. | 中文 | English | Trigger | Skill |
| --- | --- | --- | --- | --- |
| UI-25 | 緩動與時長 | Easing & Timing | Every animation | [`ui-25-easing-and-timing`](skills/ui-25-easing-and-timing/SKILL.md) |
| UI-26 | 彈性 | Spring | Any state change | [`ui-26-spring`](skills/ui-26-spring/SKILL.md) |
| UI-27 | 錯峰 | Stagger | Group entrance | [`ui-27-stagger`](skills/ui-27-stagger/SKILL.md) |

#### 滾動動效 / Scroll

Effects driven by scrolling: pinned stories, parallax, reveals, scroll-scrubbed transitions.

| No. | 中文 | English | Trigger | Skill |
| --- | --- | --- | --- | --- |
| UI-10 | 滾動螺旋流動 | Scroll-driven Helix Flow | Scroll | [`ui-10-scroll-helix-flow`](skills/ui-10-scroll-helix-flow/SKILL.md) |
| UI-12 | 滾動漩渦轉場 | Scroll-driven Vortex Transit | Scroll | [`ui-12-scroll-vortex-transit`](skills/ui-12-scroll-vortex-transit/SKILL.md) |
| UI-28 | 滾動敘事 | Scroll Storytelling | Scroll | [`ui-28-scroll-storytelling`](skills/ui-28-scroll-storytelling/SKILL.md) |
| UI-29 | 視差滾動 | Parallax | Scroll | [`ui-29-parallax`](skills/ui-29-parallax/SKILL.md) |
| UI-30 | 滾動出現 | Scroll Reveal | In view | [`ui-30-scroll-reveal`](skills/ui-30-scroll-reveal/SKILL.md) |

#### 游標與懸停 / Cursor & Hover

Effects that follow or react to the pointer: glows, tilts, magnetic pulls, lifts, cursor-driven heroes.

| No. | 中文 | English | Trigger | Skill |
| --- | --- | --- | --- | --- |
| UI-09 | 游標流光 | Cursor-driven Luminous Flow | Cursor | [`ui-09-cursor-luminous-flow`](skills/ui-09-cursor-luminous-flow/SKILL.md) |
| UI-13 | 滑過開門綻放 | Hover-triggered Door Bloom | Hover / focus | [`ui-13-hover-door-bloom`](skills/ui-13-hover-door-bloom/SKILL.md) |
| UI-14 | 游標驅動的動態主視覺 | Cursor-driven Animated Hero | Cursor / drag | [`ui-14-cursor-driven-hero`](skills/ui-14-cursor-driven-hero/SKILL.md) |
| UI-31 | 聚光 | Spotlight | Pointer move / focus | [`ui-31-spotlight`](skills/ui-31-spotlight/SKILL.md) |
| UI-32 | 3D 傾斜 | Tilt | Pointer move / drag | [`ui-32-tilt`](skills/ui-32-tilt/SKILL.md) |
| UI-33 | 磁吸 | Magnetic | Pointer near | [`ui-33-magnetic`](skills/ui-33-magnetic/SKILL.md) |
| UI-34 | 懸停上浮 | Hover Lift | Hover / focus | [`ui-34-hover-lift`](skills/ui-34-hover-lift/SKILL.md) |

#### 文字動效 / Text & Type

Headlines and numbers that move: knockout and inline-image type, scramble, typewriter, count up.

| No. | 中文 | English | Trigger | Skill |
| --- | --- | --- | --- | --- |
| UI-15 | 鏤空大標題 | Knockout Title | Scroll | [`ui-15-knockout-title`](skills/ui-15-knockout-title/SKILL.md) |
| UI-16 | 標題嵌小圖 | Inline Image Title | Tap / click | [`ui-16-inline-image-title`](skills/ui-16-inline-image-title/SKILL.md) |
| UI-35 | 亂碼解碼 | Scramble Text | In view / hover | [`ui-35-scramble-text`](skills/ui-35-scramble-text/SKILL.md) |
| UI-36 | 打字機 | Typewriter | In view / loop | [`ui-36-typewriter`](skills/ui-36-typewriter/SKILL.md) |
| UI-37 | 數字滾動 | Count Up | In view | [`ui-37-count-up`](skills/ui-37-count-up/SKILL.md) |

#### 氛圍與吸睛 / Ambient & Attention

Self-running motion that sets a mood or points at one thing: floating scenes, border beams, marquees.

| No. | 中文 | English | Trigger | Skill |
| --- | --- | --- | --- | --- |
| UI-11 | 沉浸式漂浮 | Immersive Float | Click / tap | [`ui-11-immersive-float`](skills/ui-11-immersive-float/SKILL.md) |
| UI-38 | 邊緣流光 | Border Beam | Ambient loop | [`ui-38-border-beam`](skills/ui-38-border-beam/SKILL.md) |
| UI-39 | 跑馬燈 | Marquee | Ambient loop | [`ui-39-marquee`](skills/ui-39-marquee/SKILL.md) |
| UI-41 | ASCII 鯊魚海洋 | ASCII Sharks | Ambient loop / pointer | [`ui-41-ascii-sharks`](skills/ui-41-ascii-sharks/SKILL.md) |

## 2. Tool Library / 工具庫

Tools you use to make things. Most are guides to someone else's open-source tool: they explain when to use it and how to install it, credit the original and copy none of its text. Design-12, Video-01, Video-04 and Video-05 are Lilian's own tested workflows.

### Design / 設計

In workflow order.

| No. | Skill | Job |
| --- | --- | --- |
| Design-01 | [Wireframer](skills/design-01-wireframer/SKILL.md) | Lo-fi clickable wireframes |
| Design-02 | [draw.io](skills/design-02-drawio/SKILL.md) | Editable system and flow diagrams |
| Design-03 | [Taste Pack + Hallmark + Cinematic UI](skills/design-03-taste-pack/SKILL.md) | Visual direction without the generic AI look; film-directed pages; restyles; reference boards |
| Design-04 | [Awesome DESIGN.md + design-md-chrome](skills/design-04-awesome-design-md/SKILL.md) | Borrow a proven brand's design system as a DESIGN.md, or extract one from any site, then make it your own |
| Design-05 | [UI UX Pro Max + UIZZE](skills/design-05-ui-ux-pro-max-uizze/SKILL.md) | Palettes, fonts and real-screen references |
| Design-06 | [shadcn/ui](skills/design-06-shadcn-ui/SKILL.md) | Build with React components |
| Design-07 | [Huashu + Baoyu + Open Design](skills/design-07-huashu-baoyu-open-design/SKILL.md) | Prototypes, decks and animations in one prompt; a local design workspace |
| Design-08 | [GSAP Skills](skills/design-08-gsap-skills/SKILL.md) | Scroll animation and timeline choreography in code |
| Design-09 | [PencilPlaybook](skills/design-09-pencilplaybook/SKILL.md) | Token-consistent screens on a Pencil.dev canvas |
| Design-10 | [Landing Page Generator](skills/design-10-landing-page-generator/SKILL.md) | Landing page copy and structure that converts |
| Design-11 | [MotionSites Web Builder](skills/design-11-motionsites/SKILL.md) | Cinematic heroes with real video; prompts for Lovable, Bolt and v0 |
| Design-12 | [Framer](skills/design-12-framer/SKILL.md) | Planning and building sites in Framer: layout, breakpoints, CMS, interactions, publishing |
| Design-13 | [Quality Pack](skills/design-13-quality-pack/SKILL.md) | Standards, score, polish and motion check |

### Dev & Workflow / 開發與工作流

| No. | Skill | Job |
| --- | --- | --- |
| Dev-01 | [Find Skills](skills/dev-01-find-skills/SKILL.md) | Find an existing skill before building one |
| Dev-02 | [Grill Me + Grill with Docs](skills/dev-02-grill-me/SKILL.md) | Be questioned hard until a plan has no soft spots |
| Dev-03 | [Codebase Architecture](skills/dev-03-codebase-architecture/SKILL.md) | Refactoring opportunities as a visual report |
| Dev-04 | [TDD](skills/dev-04-tdd/SKILL.md) | Build and fix test-first |
| Dev-05 | [agent-browser](skills/dev-05-agent-browser/SKILL.md) | Drive a real browser from a coding agent |
| Dev-06 | [Reddit Automation](skills/dev-06-reddit-automation/SKILL.md) | Find real demand on Reddit and draft honest, disclosed replies |

### Video & Media / 影片與媒體

| No. | Skill | Job |
| --- | --- | --- |
| Video-01 | [HyperFrames Video](skills/video-01-hyperframes-video/SKILL.md) | Lilian's tested workflow: reels, animated cards and title sequences from HTML to MP4 |
| Video-02 | [HyperFrames Pack (official)](skills/video-02-hyperframes/SKILL.md) | The official HyperFrames skills, plus music, images and voiceover. Same tool as Video-01; use one per session |
| Video-03 | [OpenFilm](skills/video-03-openfilm/SKILL.md) | Agent-made films you finish by hand in a real editor; NLE export |
| Video-04 | [Remotion Shotcraft](skills/video-04-remotion-shotcraft/SKILL.md) | Cinematic product promo videos of a website or app |
| Video-05 | [Sena & Pudding Reel Builder](skills/video-05-sena-pudding-reel-builder/SKILL.md) | Builds the Sena & Pudding English reels by script |

## 3. Learning Library / 學習庫

Turning books, courses, talks and podcasts into knowledge you can use.

| No. | Skill | Job |
| --- | --- | --- |
| Learning-01 | [cangjie-skill (仓颉)](skills/learning-01-cangjie-skill/SKILL.md) | Distil a book, course or transcript into tested, reusable Claude skills plus a digest |

## 4. References / 參考

Links to check, not skills.

- **Game UI:** curated reference sites and licence-cleared asset sources in [`game-ui-references.md`](game-ui-references.md). Downloaded assets go in [`game-assets/`](game-assets/README.md).

## Next numbers

| Category | Next |
| --- | --- |
| UI | UI-42 |
| Design | Design-14 |
| Dev & Workflow | Dev-07 |
| Video & Media | Video-06 |
| Learning | Learning-02 |

A new skill joins the category it fits and takes that category's next number; see `CONTRIBUTING.md`.

## Sources

Tool Library and Learning Library guides link to each tool's own GitHub page and name its licence, so you know where to install it from. They are written in our own words and copy none of the original's text.

## Live demo

Every UI Library skill has a working demo in `demo/`. `demo/index.html` is the gallery; each skill has its own page named like its folder (for example `demo/ui-07-drag-to-expand-and-collapse.html`), UI-15 to UI-22 are shown together on `demo/returns-bench.html`, and the sixteen motion skills UI-25 to UI-40 are also shown side by side on `demo/motion-essentials.html`. Deploy the repo on Vercel to browse them at a live link: `vercel.json` sends the site root to the gallery. Tool Library and Learning Library entries are guides, so they have no interaction demo; `demo/design-toolkit.html` is a visual field guide to the design tools they cover.

## How to use

**With Claude Code:** copy the skill folders you want into your project's `.claude/skills/` folder (or `~/.claude/skills/` to use them in every project).

**With Codex:** copy them into your project's `.agents/skills/` folder (or `~/.agents/skills/`).

**Without installing:** point the AI tool at this repository and name the skill, for example "Use UI-07 from LillianOu/ui-interaction-library to build a bottom sheet."

**By hand:** open a `SKILL.md` and paste its copy-ready prompt into any AI coding tool.

**Guide skills (Tool Library and Learning Library):** install the guide as above, then install the original tool with the commands in its `SKILL.md` (Design-04 installs a `DESIGN.md` file into your project rather than a skill). Call it by its tool name, for example "Use Quality Pack to check this page."

## Repository layout

```
skills/<category>-<NN>-<name>/SKILL.md  one folder per skill, numbered within its category
templates/SKILL-TEMPLATE.md          starting point for a new UI Library skill
templates/TOOLKIT-SKILL-TEMPLATE.md  starting point for a new guide skill
CONTRIBUTING.md                      how to add a skill and pick its category
CHANGELOG.md                         what changed and when
AGENTS.md / CLAUDE.md                rules for AI agents working in this repo
demo/                                live demos: index.html gallery, one page per skill
vercel.json                          Vercel config (root redirects to /demo/)
LICENSE                              MIT
```

## Working principles

- Describe reusable behaviours, not a single product scenario.
- Include pointer, touch, keyboard, accessibility, reduced-motion, cancellation, state, and implementation safeguards where relevant.
- Keep every skill self-contained, so it still works when copied on its own.
- Do not describe unfinished work as production-complete.
- Use each tool's real name. No renaming.

## Licence

Lilian O.'s own work in this repository is released under the [MIT licence](LICENSE). Guide skills point to other people's tools, which keep their own licences; each guide names the original's licence and links to it.
