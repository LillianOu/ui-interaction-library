---
name: 64-framer
description: Best practices, terminology, and workflow guidance for designing and building sites in Framer (the no-code web design/publishing tool) — including layout with Stacks and auto-layout, responsive breakpoints, components and variants, the Framer CMS, interactions/animations, and publishing/SEO/handoff. Use this skill whenever the user mentions Framer, is building a portfolio site, landing page, or client website in Framer, asks about Framer components/CMS/breakpoints/animations/publishing, or wants feedback/planning on a Framer project structure — even if they don't say "Framer" explicitly but describe a no-code site build. Make sure to trigger this for planning a new Framer site, structuring pages/CMS collections, choosing breakpoints, building reusable components, adding interactions, or preparing a site for launch/handoff to a client.
---

# 64 — Framer

**Category:** 技能庫 / Skill Library · 設計 / Design

Guidance for planning, structuring, and building professional sites in Framer — a no-code visual web builder that outputs real, responsive, production-grade websites. This skill treats Framer as a design + product tool, not just a drag-and-drop toy: the goal is portfolio-quality, maintainable output.

## When to go deeper vs. answer directly

- Quick terminology questions ("what's a Stack?") → answer directly, briefly.
- Planning a new site/page structure, CMS setup, component system, or pre-launch checklist → walk through the relevant section below step by step with the user, don't just dump theory.
- If the user has an existing Framer project and wants a critique, ask them to describe (or screenshot) the current structure before prescribing changes.

## Core mental model

Framer sites are built from four layers. Always help the user think in this order — most structural mistakes come from skipping straight to visuals before nailing structure:

1. **Layout primitives** — Stacks (auto-layout containers: vertical/horizontal/grid), Frames (free-position containers). Default to Stacks for anything that needs to reflow responsively; reserve Frames for deliberate absolute/overlapping positioning.
2. **Components** — reusable, variant-driven building blocks (buttons, cards, nav bars). Treat these like a lightweight design system, not one-off elements.
3. **Content** — either static (hand-placed) or dynamic via the **CMS** (Collections), used for anything repeatable: blog posts, case studies, portfolio pieces, product listings.
4. **Interactions** — scroll effects, hover/tap states, page transitions, component-level animations layered on top once structure and content are solid.

Build in that order. Don't animate a layout that isn't responsive yet.

## Responsive layout & breakpoints

- Framer's default breakpoints: **Desktop (1200px)**, **Tablet (810px)**, **Phone (390px)**. Encourage designing desktop-first for portfolio/marketing sites (most first-time visits), but always check phone — it's usually the most-trafficked breakpoint for a personal portfolio shared on social media.
- Use **Stacks with fill/fit sizing** (not fixed pixel widths) so elements reflow naturally across breakpoints instead of needing manual overrides everywhere.
- Only override a property at a smaller breakpoint when it must change (font size, direction: horizontal→vertical, padding). Framer inherits desktop values downward by default — don't rebuild each breakpoint from scratch.
- For text, use **fluid/responsive type** where possible rather than a fixed size per breakpoint, to reduce maintenance.

## Components & variants

- Anything reused more than twice (buttons, nav, cards, section headers) should become a **Component**, not a copy-pasted layer group.
- Use **Variants** for states (default/hover/active, light/dark, size options) rather than duplicate components — keeps a single source of truth.
- Expose **Component Properties** (text, image, boolean toggles, variant swaps) so the component is editable from the canvas without diving into nested layers — this matters a lot for client handoff.
- Name components and layers clearly (`Button/Primary`, `Card/Portfolio`) — Framer's layer panel and CMS field mapping both get unreadable fast without a naming convention.

## CMS (Collections)

- Use a **Collection** for any content type with 3+ repeatable items with a consistent shape: portfolio/case studies, blog posts, testimonials, product listings.
- Plan the **field schema before building the template page** — decide fields (title, cover image, category/tag, date, rich text body, external link) up front; retrofitting fields after the template is built is more painful.
- Build one **Collection Page template**, bind fields via **Connected content**, and let Framer generate individual pages automatically — don't hand-build repeat pages.
- Use **Categories/tags as CMS fields with filtering** (via CMS filter or a filter component) for portfolio sites with multiple project types, rather than separate static pages per category.
- For a design/UX portfolio specifically: a `Case Studies` collection (cover image, role, tools, summary, gallery, external link) is usually the highest-leverage CMS setup.

## Interactions & animation

- Prefer Framer's built-in **Effects** (scroll-triggered fade/slide, hover states, page transitions) before reaching for custom code overrides — they're performant and easy to maintain.
- Keep motion **purposeful and consistent**: pick 1–2 easing/duration presets and reuse them sitewide rather than a different animation style per section — this reads as more premium/intentional, which matches Lillian's brand direction (modern, minimal, premium).
- Avoid over-animating a portfolio site — recruiters/clients skimming quickly benefit from clarity over spectacle. Motion should support hierarchy (draw the eye to key work), not distract from it.
- For anything beyond built-in Effects (complex scroll-linked animation, custom cursor, canvas/WebGL elements), Framer supports **Code Components** (React) — flag this as an option but confirm the user actually wants to write/paste code before going there.

## SEO, performance & pre-launch checklist

Walk through this list with the user before they hit publish:

- **Page titles & meta descriptions** set per page (and per CMS item template) — not left as defaults.
- **Open Graph image** set for social sharing previews (portfolio links shared on LinkedIn/Threads especially).
- **Image optimization** — Framer auto-optimizes, but oversized source images still slow initial load; recommend compressing before upload if a page feels heavy.
- **Custom domain** connected (vs. the default `.framer.website` subdomain) for a professional portfolio/client site.
- **Favicon** set.
- **404 page** customized rather than left default.
- **Analytics** connected if the user wants visitor data (Framer has native analytics, or connect GA/Plausible).
- Check all breakpoints once more after final content is in — content length changes (long project titles, etc.) can break layouts that looked fine with placeholder text.

## Client handoff (for future client work)

- Use **Component Properties** and clearly named CMS fields so a client can edit content without touching layout.
- Consider Framer's **Page/Section permissions** if a client only needs edit access to specific content, not the full design.
- Document the CMS field schema briefly for the client (what each field is for) if handing off ongoing content updates.

## How to help Lillian specifically

Given her transition into AI-assisted UX/UI and product design, frame Framer work as **portfolio-quality output**, not just "getting a site up":

- Push for a clear structural plan (sitemap + CMS schema) before visual work starts.
- Flag when something is a Framer-native best practice vs. a personal aesthetic call, so she can make an informed choice.
- Suggest Code Components as a growth path — since she's also learning to code, Framer is a low-stakes place to start writing small React snippets inside a real, shipping project.
