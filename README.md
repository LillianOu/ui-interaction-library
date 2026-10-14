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

Next number: **14**.

## How to use

**With Claude Code:** copy the skill folders you want into your project's `.claude/skills/` folder (or `~/.claude/skills/` to use them in every project).

**With Codex:** copy them into your project's `.agents/skills/` folder (or `~/.agents/skills/`).

**Without installing:** point the AI tool at this repository and name the skill, for example "Use skill 07 from LillianOu/ui-interaction-library to build a bottom sheet."

**By hand:** open a `SKILL.md` and paste its copy-ready prompt into any AI coding tool.

## Repository layout

```
skills/<NN>-<name>/SKILL.md   one folder per skill, numbered in the order added
templates/SKILL-TEMPLATE.md   starting point for a new skill
CONTRIBUTING.md               how to add a skill and pick its category
CHANGELOG.md                  what changed and when
LICENSE-DECISION.md           licence status
```

## Working principles

- Describe reusable behaviours, not a single product scenario.
- Include pointer, touch, keyboard, accessibility, reduced-motion, cancellation, state, and implementation safeguards where relevant.
- Keep every skill self-contained, so it still works when copied on its own.
- Do not describe unfinished work as production-complete.

## Licence

No licence has been chosen yet. See [LICENSE-DECISION.md](LICENSE-DECISION.md).
