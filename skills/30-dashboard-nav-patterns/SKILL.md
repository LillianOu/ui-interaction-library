---
name: 30-dashboard-nav-patterns
description: Use when building or restyling an admin panel, dashboard or back-office app and the menu looks generic; pick one of six named navigation patterns (transparent nav, right rail, expanding tab, title as nav, icon rail with tooltips, quick actions) and prompt for it by its design term. Dashboard Nav Patterns (後台菜單六式) recipe with keyboard, touch and reduced-motion handling.
---
# 30 — 後台菜單六式 / Dashboard Nav Patterns

**Category:** 導覽與視圖 / Navigation & Views

## Effect

The menu stops looking like a default sidebar. Each of the six patterns changes where navigation sits and how the current page is marked, so the first screen reads as one designed composition instead of "sidebar + cards". The skill gives every pattern a name, a short spec and a prompt, because naming the pattern by its design term is what gets an AI tool to build it instead of falling back to a generic left sidebar.

## When to use

Use when a dashboard, admin, analytics, CRM, logistics, booking or internal-tool screen needs a more considered navigation. Choose one pattern per product; do not mix several on one screen except 06, which pairs with any icon rail. This skill is an interaction recipe, not an existing code component.

| No. | Term | 中文 | Best for | Key spec |
| --- | --- | --- | --- | --- |
| 01 | Transparent Nav | 透明頂欄 | First screen with a gradient, photo or tinted background | Bar background 0%, no divider, active item is a frosted glass pill |
| 02 | Right Rail | 右側豎軌 | Boards, calendars and kanban that need the full left width | Full-height rail on the right, ~60px, bright brand fill, active item dark rounded tile, "New" pinned on top |
| 03 | Expanding Tab | 當前項展開文字 | Top bar with more destinations than labels can fit | Icons only; the active item widens (~126px) to show its label; spring width transition |
| 04 | Title as Nav | 圖標菜單配大標題 | Data-heavy pages where people lose track of where they are | Icon rail ~60px; the current page name becomes a ~40px page title with a scope picker beside it; title swaps when the icon changes |
| 05 | Icon Rail + Tooltip | 圖標軌加懸停提示 | Many sections, power users, dense dashboards | Icon rail ~72–92px, label tooltip on the right on hover or focus, icons grouped by dividers |
| 06 | Quick Actions | 快捷操作 | Frequent tasks that should not need a page change | Column of round buttons beside the menu, the most-used one in the primary colour, runs in place |

## Interaction contract

- Input: mouse, touch, pen and keyboard for every pattern. Tooltips (05) open on hover and on keyboard focus and are never the only way to learn a label on touch: on touch, long-press shows the tooltip, and the current page title (or a visible label on the active item) always names where you are.
- States per item: **default**, **hover**, **focus-visible**, **active/current**, **pressed**, **disabled**, and for 06 **running** and **done/failed** (an action shows progress on the button, then a short confirmation or error toast).
- Current page: exactly one item carries the active style and `aria-current="page"`. In 04 the page title is the `h1` and updates in the same frame as the active icon.
- Expanding Tab (03): only the active item shows its label; width animates from icon size to the label width; other items stay square. The active label never truncates; if it would, the bar scrolls or the label shortens.
- Transparent Nav (01): text and icons must keep 4.5:1 contrast against whatever sits behind the bar. When the page scrolls under it, add a subtle blur or tint so contrast holds; the bar stays transparent at the top.
- Right Rail (02): the rail is fixed, full height; content scrolls independently. Keyboard tab order still starts with the main navigation (place it first in the DOM, position it right with CSS), or offer a skip link.
- Quick Actions (06): actions execute without navigating. Destructive actions need confirmation or undo. Disable a button while it runs to prevent double triggers.
- Edge cases: narrow screens (below ~768px) turn rails (02, 04, 05) into a bottom tab bar or a compact top bar; 03 keeps icons with the active label; 06 moves into a floating action button with a small menu. Long or translated labels, a 44px minimum hit area, and badges (counts) that do not shift layout.
- Accessibility: wrap navigation in `<nav aria-label="Main">`; icon-only items need an accessible name (`aria-label` or visually hidden text), not just the tooltip; tooltips use `role="tooltip"` linked with `aria-describedby` and close on Escape; quick actions are `<button>`s with labels, and results are announced through an `aria-live="polite"` region.
- Reduced motion: replace the spring width change (03), tooltip slide (05) and pill slide (01) with instant swaps or a short opacity fade.

## Implementation notes

- Shared active marker: one absolutely positioned "pill" element that moves to the active item (measure with `getBoundingClientRect`, or Framer Motion `layoutId`), rather than toggling a background on each item; this gives the smooth slide in 01, 02 and 03.
- 01: `background: transparent; border: 0` on the bar; active pill `background: rgba(255,255,255,.55); backdrop-filter: blur(12px); border-radius: 999px`. Add a scroll listener (or `IntersectionObserver` on a sentinel) that applies a tint once content passes under the bar.
- 02 / 04 / 05: CSS grid shell, for example `grid-template-columns: 1fr 60px` for a right rail or `72px 1fr` for a left rail, `height: 100dvh`, with the content column `overflow: auto`.
- 03: animate `width` or `grid-template-columns` on the active item with a spring (stiffness ~400, damping ~30) or the CSS `linear()` spring easing; measure label width once and cache it.
- 04: drive the title from the same route state as the rail (`<h1>{currentPage.title}</h1>`); the scope picker (warehouse, date range, team) sits on the title baseline.
- 05: position tooltips with Floating UI or CSS anchor positioning; 300–500ms hover delay, no delay on focus; group dividers are `<hr>` or `role="separator"` between `<ul>` groups.
- 06: keep actions in a small config (`{ id, label, icon, primary, run }`); at most one primary; show at most 4 in the column and put the rest in "More".
- Theme: define rail colour, active colour and primary colour as tokens so a product can swap the bright rail (02) or lime primary (06) for its own brand.
- Avoid: icon-only navigation with no labels anywhere, hiding the current page, using tooltips for essential information, animating layout properties on every frame without `requestAnimationFrame`, and mixing more than one main navigation pattern on a page.

## Prompt terms

Name the pattern in the prompt; the term is what steers the AI tool. Short prompts, written for this library:

| No. | English prompt line | 中文提示詞 |
| --- | --- | --- |
| 01 | Make the top bar a Transparent Nav: no background and no divider, labels sit straight on the page background, the current item gets a semi-transparent white rounded pill. | 導航改成透明頂欄（Transparent Nav）：不要底色和分隔線，文字直接放在頁面背景上，當前項加半透明白色圓角底。 |
| 02 | Move the main navigation to a Right Rail: a full-height vertical icon rail on the right in a bright brand colour, the current item on a dark rounded tile, the New button pinned at the top. | 主導航移到右側豎軌（Right Rail）：通高的直向圖標軌，整條用亮色，當前項用深色圓角底，新建按鈕固定在頂部。 |
| 03 | Make the top navigation an Expanding Tab group: icons only, the current item expands to show its label, and the width changes with a spring ease. | 頂部導航做成展開式圖標組（Expanding Tab）：只放圖標，當前項展開顯示文字，寬度變化用彈性緩動。 |
| 04 | Use Title as Nav: collapse the sidebar to an icon rail, show the current page name as a large page title with a scope picker beside it, and swap the title when the icon changes. | 用大標題當導航（Title as Nav）：側邊欄收成純圖標軌，當前頁名放大成頁面大標題，旁邊接範圍選擇，切換圖標時標題同步更換。 |
| 05 | Make the sidebar an Icon Rail with tooltips: icons only, a label tooltip opens to the right on hover and focus, and dividers split the icons into groups. | 側邊欄做成圖標軌（Icon Rail）：只放圖標，懸停或聚焦時右側彈出文字提示（Tooltip），用分隔線把圖標分組。 |
| 06 | Add a Quick Actions column beside the menu: round buttons stacked vertically, the most-used one in the primary colour, each runs in place without leaving the page. | 菜單旁加一列快捷操作（Quick Actions）：圓形按鈕縱向排列，最常用的一個用主色，點擊直接執行，不跳轉頁面。 |

## Acceptance criteria

1. The chosen pattern matches its key spec in the table above, with exactly one current item marked visually and with `aria-current="page"`.
2. Every icon-only item has an accessible name; labels are reachable on touch without hover.
3. Navigation works fully with keyboard: Tab order, visible focus, Enter/Space to activate, Escape closes tooltips and menus.
4. Transparent and bright-rail variants keep 4.5:1 text contrast in light and dark themes.
5. Quick actions run without navigation, show running and result states, and cannot double-fire.
6. Reduced-motion mode swaps states without spring or slide motion.
7. Rails adapt to a bottom or top bar below ~768px; responsive at 375px, 768px and 1440px; no console errors, listeners cleaned up.

## Copy-ready English prompt

```text
Build a reusable dashboard navigation shell that supports six named patterns, selected by a `variant` prop: "transparent-nav", "right-rail", "expanding-tab", "title-as-nav", "icon-rail-tooltip" and "quick-actions" (the last one is an add-on column that can sit beside any icon rail).
- Transparent Nav: top bar with no background or divider, labels on the page background, the current item on a semi-transparent white rounded pill; add a light blur tint only once content scrolls underneath so contrast stays at 4.5:1.
- Right Rail: full-height 60px vertical icon rail on the right in a bright brand colour, current item on a dark rounded tile, a New button pinned at the top, content scrolling independently; keep the nav first in the DOM.
- Expanding Tab: icon-only top bar where the current item expands to show its label, width animated with a spring.
- Title as Nav: 60px icon rail, the current page name rendered as a large h1 with a scope picker beside it, updated together with the active icon.
- Icon Rail + Tooltip: icon rail with label tooltips on the right on hover (short delay) and on keyboard focus (no delay), role="tooltip" with aria-describedby, Escape to close, long-press on touch, and dividers grouping the icons.
- Quick Actions: round buttons stacked vertically next to the menu, at most four, the most-used one in the primary colour; each runs in place without navigating, shows running then success or error, is disabled while running, and announces results in an aria-live region.
Use one moving active pill for the current item, `aria-current="page"`, accessible names on every icon button, 44px minimum hit areas, and colour tokens for rail, active and primary colours. Below 768px turn rails into a bottom tab bar. With prefers-reduced-motion, swap states without spring or slide motion. Expose items (id, label, icon, group, badge), current id, actions and variant as props.
```

## Source

Inspired by a short video on six premium dashboard menu patterns for AI-assisted design (我叫-西瓜同学, 2026). Written in our own words, with full interaction contracts added.
