# Adding a skill

1. Pick the next unused number (see "Next number" in the README).
2. Copy `templates/SKILL-TEMPLATE.md` to `skills/<NN>-<kebab-case-name>/SKILL.md`.
3. Set `name` in the frontmatter to exactly the folder name, for example `14-cursor-driven-hero`.
4. Write `description` as one sentence that starts with "Use when…", so AI tools know when to pick the skill.
5. Give the title both names: `# 14 — 中文名稱 / English Name`.
6. Choose one category (below), write it on the `**Category:**` line, and fill in every section of the template.
7. UI Library skills only — build a demo: copy `demo/_template.html` to `demo/<NN>-<name>.html` (same name as the skill folder), build the interaction in it using the tokens in `demo/assets/demo.css`, fix the prev/next links of its neighbours, and add a card for it in `demo/index.html`. Check it at 375px and with reduced motion.
8. Add a row to the matching category table in `README.md`, update "Next number", and add a line to `CHANGELOG.md`, all in the same change.

Keep commits small and descriptive. Do not add private client, employer, health, account or analytics data.

## Categories

Skills sit on shelves inside the Library's sections (UI Library, Skill Library, Learning Library). Pick the one category that fits best; numbers never change when a skill is filed.

| Shelf | Category | Use for |
| --- | --- | --- |
| 版面 / Layout | 導覽與視圖 / Navigation & Views | Moving between views and pages: expanding cards, sheets, tabs, menus, carousels |
| 版面 / Layout | 網格與面板 / Grids & Panels | Arranging and rearranging content: reorderable lists, reflowing grids, columns, rails, resizable splits |
| 元件 / Components | 輸入與控制 / Inputs & Controls | Entering or choosing a value: fields, pickers, sliders, steppers, swipes |
| 元件 / Components | 回饋與載入 / Feedback & Loading | Confirming actions and showing loading, success, error or progress |
| 動效 / Motion | 動效基礎 / Motion Foundations | The rules behind all motion: easing, duration, spring physics, stagger |
| 動效 / Motion | 滾動動效 / Scroll | Effects driven by scrolling: pinned stories, parallax, reveals, scroll-scrubbed transitions |
| 動效 / Motion | 游標與懸停 / Cursor & Hover | Effects that follow or react to the pointer: glows, tilts, magnetic pulls, lifts, cursor-driven heroes |
| 動效 / Motion | 文字動效 / Text & Type | Headlines and numbers that move: knockout and inline-image type, scramble, typewriter, count up |
| 動效 / Motion | 氛圍與吸睛 / Ambient & Attention | Self-running motion that sets a mood or points at one thing: floating scenes, border beams, marquees |
| 技能庫 / Skill Library | 設計 / Design | Design tools, one job each, listed in workflow order |
| 技能庫 / Skill Library | 開發與工作流 / Dev & Workflow | Tools for planning, coding, testing, browsing and marketing |
| 技能庫 / Skill Library | 影片與媒體 / Video & Media | Tools that make videos, reels and media |
| 學習庫 / Learning Library | 學習 / Learning | Tools that turn books, courses, talks and transcripts into usable knowledge |

Motion skills take their durations and curves from 45 Easing & Timing. If a new skill fits none of these categories, add a category to this table, the README and the demo gallery in the same change.

## Adding a guide skill (Skill Library or Learning Library)

Guide skills guide people and AI tools to someone else's skill; they never copy it.

1. Copy `templates/TOOLKIT-SKILL-TEMPLATE.md` instead of the interaction template.
2. Name the folder `<NN>-<tool-name>` and title it `# NN — Tool Name`, using the tool's real name. Do not invent character or nickname names.
3. Only wrap skills under an open licence (MIT, Apache-2.0 or similar). Link the source, name the licence, and record the date and commit you checked.
4. Write the guide in your own words. Do not paste text, rules or prompts from the original skill.
5. Give it one clear job. If it overlaps an existing guide skill, add it to that guide's routing table instead of creating a new entry.

If a new skill fits none of these, add a new category to this table and to the README in the same change.

## Quality check

Before committing, confirm that:

- the skill describes a reusable interaction, not one portfolio-specific screen;
- it covers mouse, touch, keyboard, accessibility, reduced motion, cancellation and edge states where relevant;
- it works on its own when copied without the rest of the library;
- it does not promise a production-ready implementation unless one exists.
