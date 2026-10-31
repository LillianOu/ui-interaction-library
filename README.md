# Lilian O. — Library

Every skill Lilian O. uses, in one place, sorted by category. Each entry is a self-contained `SKILL.md` that people can read and AI tools (Claude, Claude Code, Codex, Cursor) can use directly.

**For AI agents:** read this page first, then open the `SKILL.md` of the entry you need. Agent rules are in [`AGENTS.md`](AGENTS.md).

```
Library
├── 1. UI Library        interactions and motion to build into pages and apps   (01–14, 22–30, 43, 45–60)
├── 2. Skill Library     tools that help with the work
│   ├── Design           (15–21, 31–35, 64)
│   ├── Dev & Workflow   (36–40, 42)
│   └── Video & Media    (41, 44, 62, 63, 65)
├── 3. Learning Library  turning books, courses and talks into usable knowledge  (61)
└── 4. References        links to check, not skills
```

Numbers are permanent IDs in the order skills were added, so they jump around inside a category. Every skill folder sits flat in `skills/` so AI tools can find it. Tool skills keep their real tool names.

## 1. UI Library / UI 介面庫

Reusable interactions and motion effects. Each is an implementation recipe with accessibility and fallback rules and a copy-ready prompt, not finished code. Every one has a live demo (see [Live demo](#live-demo)).

| Shelf | Categories |
| --- | --- |
| 版面 / Layout | 導覽與視圖 Navigation & Views (5) · 網格與面板 Grids & Panels (5) |
| 元件 / Components | 輸入與控制 Inputs & Controls (4) · 回饋與載入 Feedback & Loading (3) |
| 動效 / Motion | 動效基礎 Motion Foundations (3) · 滾動動效 Scroll (5) · 游標與懸停 Cursor & Hover (7) · 文字動效 Text & Type (5) · 氛圍與吸睛 Ambient & Attention (3) |

### 版面 / Layout

How the page is arranged and how you move around it.

#### 導覽與視圖 / Navigation & Views

Moving between views and pages: expanding cards, sheets, tabs, menus, carousels.

| No. | 中文 | English | Trigger | Skill |
| --- | --- | --- | --- | --- |
| 01 | 共享元素展開 | Shared Element Expansion | Tap | [`01-shared-element-expansion`](skills/01-shared-element-expansion/SKILL.md) |
| 07 | 拖曳展開與收合 | Drag to Expand & Collapse | Drag | [`07-drag-to-expand-and-collapse`](skills/07-drag-to-expand-and-collapse/SKILL.md) |
| 27 | 檔案夾標籤頁 | Folder Tabs | Tap / keyboard | [`27-folder-tabs`](skills/27-folder-tabs/SKILL.md) |
| 30 | 後台菜單六式 | Dashboard Nav Patterns (Transparent Nav · Right Rail · Expanding Tab · Title as Nav · Icon Rail · Quick Actions) | Tap / keyboard | [`30-dashboard-nav-patterns`](skills/30-dashboard-nav-patterns/SKILL.md) |
| 43 | 卡片展開輪播 | Card-to-Hero Carousel | Click / tap / swipe | [`43-card-to-hero-carousel`](skills/43-card-to-hero-carousel/SKILL.md) |

#### 網格與面板 / Grids & Panels

Arranging and rearranging content: reorderable lists, reflowing grids, columns, rails, resizable splits.

| No. | 中文 | English | Trigger | Skill |
| --- | --- | --- | --- | --- |
| 06 | 拖曳排序 | Drag to Reorder | Drag | [`06-drag-to-reorder`](skills/06-drag-to-reorder/SKILL.md) |
| 24 | 點一格撐成通欄 | Expanding Grid | Tap / click | [`24-expanding-grid`](skills/24-expanding-grid/SKILL.md) |
| 25 | 兩列錯速滾動 | Offset Columns | Scroll | [`25-offset-columns`](skills/25-offset-columns/SKILL.md) |
| 26 | 左欄日期吸頂 | Sticky Date Rail | Scroll | [`26-sticky-date-rail`](skills/26-sticky-date-rail/SKILL.md) |
| 29 | 拖動分屏比例 | Split View | Drag / keyboard | [`29-split-view`](skills/29-split-view/SKILL.md) |

### 元件 / Components

Things people touch, and what they get back.

#### 輸入與控制 / Inputs & Controls

Entering or choosing a value: fields, pickers, sliders, steppers, swipes.

| No. | 中文 | English | Trigger | Skill |
| --- | --- | --- | --- | --- |
| 02 | 彈性數值調節 | Elastic Value Adjustment | Drag | [`02-elastic-value-adjustment`](skills/02-elastic-value-adjustment/SKILL.md) |
| 03 | 滑動選擇 | Swipe Selection | Swipe | [`03-swipe-selection`](skills/03-swipe-selection/SKILL.md) |
| 05 | 浮動標籤 | Floating Label | Type | [`05-floating-label`](skills/05-floating-label/SKILL.md) |
| 28 | 圓泡堆疊選擇 | Bubble Picker | Tap / keyboard | [`28-bubble-picker`](skills/28-bubble-picker/SKILL.md) |

#### 回饋與載入 / Feedback & Loading

Confirming actions and showing loading, success, error or progress.

| No. | 中文 | English | Trigger | Skill |
| --- | --- | --- | --- | --- |
| 04 | 動態狀態切換 | Animated State Transition | Tap | [`04-animated-state-transition`](skills/04-animated-state-transition/SKILL.md) |
| 08 | 飛向目標的回饋 | Fly-to-Target Feedback | Tap | [`08-fly-to-target-feedback`](skills/08-fly-to-target-feedback/SKILL.md) |
| 60 | 流光 | Shimmer | Loading / ambient | [`60-shimmer`](skills/60-shimmer/SKILL.md) |

### 動效 / Motion

Motion grouped by what triggers it. Start with Motion Foundations: its timing rules apply to every other entry.

#### 動效基礎 / Motion Foundations

The rules behind all motion: easing, duration, spring physics, stagger.

| No. | 中文 | English | Trigger | Skill |
| --- | --- | --- | --- | --- |
| 45 | 緩動與時長 | Easing & Timing | Every animation | [`45-easing-and-timing`](skills/45-easing-and-timing/SKILL.md) |
| 46 | 彈性 | Spring | Any state change | [`46-spring`](skills/46-spring/SKILL.md) |
| 47 | 錯峰 | Stagger | Group entrance | [`47-stagger`](skills/47-stagger/SKILL.md) |

#### 滾動動效 / Scroll

Effects driven by scrolling: pinned stories, parallax, reveals, scroll-scrubbed transitions.

| No. | 中文 | English | Trigger | Skill |
| --- | --- | --- | --- | --- |
| 10 | 滾動螺旋流動 | Scroll-driven Helix Flow | Scroll | [`10-scroll-helix-flow`](skills/10-scroll-helix-flow/SKILL.md) |
| 12 | 滾動漩渦轉場 | Scroll-driven Vortex Transit | Scroll | [`12-scroll-vortex-transit`](skills/12-scroll-vortex-transit/SKILL.md) |
| 48 | 滾動敘事 | Scroll Storytelling | Scroll | [`48-scroll-storytelling`](skills/48-scroll-storytelling/SKILL.md) |
| 49 | 視差滾動 | Parallax | Scroll | [`49-parallax`](skills/49-parallax/SKILL.md) |
| 50 | 滾動出現 | Scroll Reveal | In view | [`50-scroll-reveal`](skills/50-scroll-reveal/SKILL.md) |

#### 游標與懸停 / Cursor & Hover

Effects that follow or react to the pointer: glows, tilts, magnetic pulls, lifts, cursor-driven heroes.

| No. | 中文 | English | Trigger | Skill |
| --- | --- | --- | --- | --- |
| 09 | 游標流光 | Cursor-driven Luminous Flow | Cursor | [`09-cursor-luminous-flow`](skills/09-cursor-luminous-flow/SKILL.md) |
| 13 | 滑過開門綻放 | Hover-triggered Door Bloom | Hover / focus | [`13-hover-door-bloom`](skills/13-hover-door-bloom/SKILL.md) |
| 14 | 游標驅動的動態主視覺 | Cursor-driven Animated Hero | Cursor / drag | [`14-cursor-driven-hero`](skills/14-cursor-driven-hero/SKILL.md) |
| 51 | 聚光 | Spotlight | Pointer move / focus | [`51-spotlight`](skills/51-spotlight/SKILL.md) |
| 52 | 3D 傾斜 | Tilt | Pointer move / drag | [`52-tilt`](skills/52-tilt/SKILL.md) |
| 53 | 磁吸 | Magnetic | Pointer near | [`53-magnetic`](skills/53-magnetic/SKILL.md) |
| 54 | 懸停上浮 | Hover Lift | Hover / focus | [`54-hover-lift`](skills/54-hover-lift/SKILL.md) |

#### 文字動效 / Text & Type

Headlines and numbers that move: knockout and inline-image type, scramble, typewriter, count up.

| No. | 中文 | English | Trigger | Skill |
| --- | --- | --- | --- | --- |
| 22 | 鏤空大標題 | Knockout Title | Scroll | [`22-knockout-title`](skills/22-knockout-title/SKILL.md) |
| 23 | 標題嵌小圖 | Inline Image Title | Tap / click | [`23-inline-image-title`](skills/23-inline-image-title/SKILL.md) |
| 55 | 亂碼解碼 | Scramble Text | In view / hover | [`55-scramble-text`](skills/55-scramble-text/SKILL.md) |
| 56 | 打字機 | Typewriter | In view / loop | [`56-typewriter`](skills/56-typewriter/SKILL.md) |
| 57 | 數字滾動 | Count Up | In view | [`57-count-up`](skills/57-count-up/SKILL.md) |

#### 氛圍與吸睛 / Ambient & Attention

Self-running motion that sets a mood or points at one thing: floating scenes, border beams, marquees.

| No. | 中文 | English | Trigger | Skill |
| --- | --- | --- | --- | --- |
| 11 | 沉浸式漂浮 | Immersive Float | Click / tap | [`11-immersive-float`](skills/11-immersive-float/SKILL.md) |
| 58 | 邊緣流光 | Border Beam | Ambient loop | [`58-border-beam`](skills/58-border-beam/SKILL.md) |
| 59 | 跑馬燈 | Marquee | Ambient loop | [`59-marquee`](skills/59-marquee/SKILL.md) |

## 2. Skill Library / 技能庫

Tools that help with the work. Most are guides to someone else's open-source skill: they explain when to use it and how to install it, credit the original and copy none of its text. Skills 62–65 are Lilian's own tested workflows.

### Design / 設計

In workflow order.

| No. | Skill | Job |
| --- | --- | --- |
| 15 | [Wireframer](skills/15-wireframer/SKILL.md) | Lo-fi clickable wireframes |
| 16 | [draw.io](skills/16-drawio/SKILL.md) | Editable system and flow diagrams |
| 17 | [Taste Pack + Hallmark + Cinematic UI](skills/17-taste-pack/SKILL.md) | Visual direction without the generic AI look; film-directed pages; restyles; reference boards |
| 31 | [Awesome DESIGN.md + design-md-chrome](skills/31-awesome-design-md/SKILL.md) | Borrow a proven brand's design system as a DESIGN.md, or extract one from any site, then make it your own |
| 18 | [UI UX Pro Max + UIZZE](skills/18-ui-ux-pro-max-uizze/SKILL.md) | Palettes, fonts and real-screen references |
| 19 | [shadcn/ui](skills/19-shadcn-ui/SKILL.md) | Build with React components |
| 20 | [Huashu + Baoyu + Open Design](skills/20-huashu-baoyu-open-design/SKILL.md) | Prototypes, decks and animations in one prompt; a local design workspace |
| 32 | [GSAP Skills](skills/32-gsap-skills/SKILL.md) | Scroll animation and timeline choreography in code |
| 33 | [PencilPlaybook](skills/33-pencilplaybook/SKILL.md) | Token-consistent screens on a Pencil.dev canvas |
| 34 | [Landing Page Generator](skills/34-landing-page-generator/SKILL.md) | Landing page copy and structure that converts |
| 35 | [MotionSites Web Builder](skills/35-motionsites/SKILL.md) | Cinematic heroes with real video; prompts for Lovable, Bolt and v0 |
| 64 | [Framer](skills/64-framer/SKILL.md) | Planning and building sites in Framer: layout, breakpoints, CMS, interactions, publishing |
| 21 | [Quality Pack](skills/21-quality-pack/SKILL.md) | Standards, score, polish and motion check |

### Dev & Workflow / 開發與工作流

| No. | Skill | Job |
| --- | --- | --- |
| 36 | [Find Skills](skills/36-find-skills/SKILL.md) | Find an existing skill before building one |
| 37 | [Grill Me + Grill with Docs](skills/37-grill-me/SKILL.md) | Be questioned hard until a plan has no soft spots |
| 38 | [Codebase Architecture](skills/38-codebase-architecture/SKILL.md) | Refactoring opportunities as a visual report |
| 39 | [TDD](skills/39-tdd/SKILL.md) | Build and fix test-first |
| 40 | [agent-browser](skills/40-agent-browser/SKILL.md) | Drive a real browser from a coding agent |
| 42 | [Reddit Automation](skills/42-reddit-automation/SKILL.md) | Find real demand on Reddit and draft honest, disclosed replies |

### Video & Media / 影片與媒體

| No. | Skill | Job |
| --- | --- | --- |
| 62 | [HyperFrames Video](skills/62-hyperframes-video/SKILL.md) | Lilian's tested workflow: reels, animated cards and title sequences from HTML to MP4 |
| 41 | [HyperFrames Pack (official)](skills/41-hyperframes/SKILL.md) | The official HyperFrames skills, plus music, images and voiceover. Same tool as 62; use one per session |
| 44 | [OpenFilm](skills/44-openfilm/SKILL.md) | Agent-made films you finish by hand in a real editor; NLE export |
| 63 | [Remotion Shotcraft](skills/63-remotion-shotcraft/SKILL.md) | Cinematic product promo videos of a website or app |
| 65 | [Sena & Pudding Reel Builder](skills/65-sena-pudding-reel-builder/SKILL.md) | Builds the Sena & Pudding English reels by script |

## 3. Learning Library / 學習庫

Turning books, courses, talks and podcasts into knowledge you can use.

| No. | Skill | Job |
| --- | --- | --- |
| 61 | [cangjie-skill (仓颉)](skills/61-cangjie-skill/SKILL.md) | Distil a book, course or transcript into tested, reusable Claude skills plus a digest |

## 4. References / 參考

Links to check, not skills.

- **Game UI:** curated reference sites and licence-cleared asset sources in [`game-ui-references.md`](game-ui-references.md). Downloaded assets go in [`game-assets/`](game-assets/README.md).

Next number: **66**. Numbers 01–65 are all in use. New skills take the next number and join whichever category fits; see `CONTRIBUTING.md`.

## Live demo

Every UI Library skill has a working demo in `demo/`. `demo/index.html` is the gallery; each skill has its own page named like its folder (for example `demo/07-drag-to-expand-and-collapse.html`), skills 22–29 are shown together on `demo/returns-bench.html`, and the sixteen motion skills 45–60 are also shown side by side on `demo/motion-essentials.html`. Deploy the repo on Vercel to browse them at a live link: `vercel.json` sends the site root to the gallery. Skill Library and Learning Library entries are guides, so they have no interaction demo; `demo/design-toolkit.html` is a visual field guide to the design tools they cover.

## How to use

**With Claude Code:** copy the skill folders you want into your project's `.claude/skills/` folder (or `~/.claude/skills/` to use them in every project).

**With Codex:** copy them into your project's `.agents/skills/` folder (or `~/.agents/skills/`).

**Without installing:** point the AI tool at this repository and name the skill, for example "Use skill 07 from LillianOu/ui-interaction-library to build a bottom sheet."

**By hand:** open a `SKILL.md` and paste its copy-ready prompt into any AI coding tool.

**Guide skills (Skill Library and Learning Library):** install the guide as above, then install the original tool with the commands in its `SKILL.md` (31 installs a `DESIGN.md` file into your project rather than a skill). Call it by its tool name, for example "Use Quality Pack to check this page."

## Repository layout

```
skills/<NN>-<name>/SKILL.md          one folder per skill, numbered in the order added
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
