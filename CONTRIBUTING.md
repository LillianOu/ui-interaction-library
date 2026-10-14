# Adding a skill

1. Pick the next unused number (see "Next number" in the README).
2. Copy `templates/SKILL-TEMPLATE.md` to `skills/<NN>-<kebab-case-name>/SKILL.md`.
3. Set `name` in the frontmatter to exactly the folder name, for example `14-cursor-driven-hero`.
4. Write `description` as one sentence that starts with "Use when…", so AI tools know when to pick the skill.
5. Give the title both names: `# 14 — 中文名稱 / English Name`.
6. Choose one category (below) and fill in every section of the template.
7. Add a row to the matching category table in `README.md`, update "Next number", and add a line to `CHANGELOG.md`, all in the same change.

Keep commits small and descriptive. Do not add private client, employer, health, account or analytics data.

## Categories

| Category | Use for |
| --- | --- |
| 版面與導覽 / Layout & Navigation | Moving between views, rearranging content, panels, sheets and drawers |
| 輸入與控制 / Input & Controls | Form fields, pickers, sliders, steppers and other ways to enter a value |
| 回饋與狀態 / Feedback & State | Confirming actions and showing loading, success, error or progress |
| 動態視覺效果 / Motion Effects | Expressive cursor, scroll, hover or ambient visuals such as heroes and transitions |

If a new skill fits none of these, add a new category to this table and to the README in the same change.

## Quality check

Before committing, confirm that:

- the skill describes a reusable interaction, not one portfolio-specific screen;
- it covers mouse, touch, keyboard, accessibility, reduced motion, cancellation and edge states where relevant;
- it works on its own when copied without the rest of the library;
- it does not promise a production-ready implementation unless one exists.
