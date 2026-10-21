---
name: 26-sticky-date-rail
description: Use when a schedule, itinerary, timeline or feed grouped by day should keep an oversized date pinned in a narrow left rail, with the next day's date pushing the old one out as you scroll. Sticky Date Rail (左欄日期吸頂) recipe with accessibility and reduced-motion handling.
---
# 26 — 左欄日期吸頂 / Sticky Date Rail

**Category:** 排版互動 / Layout Relationships

## Effect

A schedule page with two columns: a narrow left rail that holds an oversized day number and weekday, and a wider right column listing that day's items. As the reader scrolls, the current date stays stuck at the top of the rail. When the next day's group arrives, its date rises from below and physically pushes the previous one up and out, so there is always exactly one clear "today" label without any jump.

## When to use

Use for itineraries, event programmes, booking calendars, habit or KPI logs, order histories, changelogs and chat archives grouped by date or by any heading (month, chapter, step). Works when each group has several items so the date has time to stick. This skill is an interaction recipe, not an existing code component.

## Interaction contract

- Input: normal scroll from wheel, trackpad, touch, keyboard and scrollbar. Optional: tapping a date jumps to that day's first item.
- States per date label: **below** (scrolling in with its group), **stuck** (pinned at the top of the rail), **being pushed** (moving up as the next label meets it), **gone**. Only one label is fully stuck at any time.
- Edge cases: a day with a single short item (the label must still be readable; give each group a minimum height equal to the label height), today's date highlighted, empty days either hidden or shown as "No plans", loading more days at the end, a header bar of variable height (use its height as the sticky top offset).
- Accessibility: each day is a section with a real heading (for example "Tuesday 15 October") that includes the full date, even when only "15 TUE" is shown visually; use `<time datetime>`. The list order in the DOM matches visual order. The stuck label is not duplicated for screen readers.
- Reduced motion: native sticky positioning already involves no added animation; keep it, but drop any extra fades or scale effects on the label.

## Implementation notes

- The push effect comes for free with CSS: put each date label inside its own day group (`<section>` with the rail cell and the items), and give the label `position: sticky; top: <header height>`. A sticky element can never leave its parent, so when the group ends, the label is carried up while the next group's label arrives and takes its place.
- Layout: `display: grid; grid-template-columns: <rail width> 1fr` per section, rail width about 22–28% on mobile. The label uses a very large tabular-figure numeral with a small spaced weekday underneath, plus a short accent bar for the active day.
- Optional polish: use an `IntersectionObserver` (or scroll-driven animation) to mark the currently stuck label as active (accent colour, full opacity) and dim the incoming one until it sticks.
- Do not use JavaScript scroll handlers to position labels; they flicker and fight the browser.
- Watch for `overflow: hidden` on any ancestor, which silently breaks `position: sticky`.

## Acceptance criteria

1. The current day's date stays pinned at the top of the rail while its items scroll.
2. The next date pushes the previous one out smoothly with no overlap, flicker or gap.
3. Works with native scrolling on mobile Safari, Chrome and Firefox, including inside a scroll container.
4. Each group has a full, readable heading for assistive tech; DOM order equals visual order.
5. Short groups, empty days and late-loaded days behave correctly.
6. Responsive at 375px, 768px and 1440px.

## Copy-ready English prompt

```text
Create a reusable sticky date rail for a schedule or itinerary. Lay each day out as a section with two columns: a narrow left rail holding an oversized day number in tabular figures, a small letter-spaced weekday and a short accent bar, and a wider right column listing that day's items as cards with time, title and optional thumbnail. Make each date label position: sticky at the top of its own section (offset by any header height), so it stays pinned while its day scrolls and is pushed up and out by the next day's label when the next section arrives, with no JavaScript positioning. Give each section a minimum height so short days still show their date. Mark the currently stuck date as active with an IntersectionObserver. Give every section a real heading with the full date and a time element for screen readers, keep DOM order equal to visual order, and avoid overflow: hidden on ancestors. Optional: tapping a date scrolls to that day. With prefers-reduced-motion, keep native sticky behaviour without extra fades. Expose the grouped data, rail width, header offset and date format as props.
```
