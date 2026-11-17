---
name: design-17-motion-design-skill
description: Use when any animation (UI transition, micro-interaction, loading state, scroll effect, illustration or brand motion) should follow professional motion principles for timing, easing and choreography, whatever library builds it. Routes to LottieFiles' motion-design skill.
---
# Design-17 — motion-design-skill

**Category:** 工具庫 / Tool Library · 設計 / Design
**Powered by:** [LottieFiles/motion-design-skill](https://github.com/LottieFiles/motion-design-skill) `motion-design` (MIT: free to use, change and share, including commercially, as long as the licence notice is kept)

> This skill is a guide, not a copy. It explains when to call an external skill, how to install it and how to get good results. It contains none of the original skill's text; install the original to use it.

## What it does

motion-design gives an AI agent the judgement of a motion designer. Before it animates anything, it decides what the motion is for, what actually moves, how long it should take and how it should ease in and out, and how several elements should be staggered so the result feels intentional rather than random. It adapts classic animation principles for interfaces and works with any animation system: CSS, Framer Motion, GSAP, Lottie or springs.

## When to use

- Use whenever you ask an AI to animate buttons, cards, modals, page transitions, loading, success or error states.
- Use to set a consistent motion personality for a brand or product (calm, playful, premium).
- Use as a second pass when an animation an AI built feels stiff, floaty or too busy.
- Do not use to name or browse moves. Use Design-15 Motion Prompt.
- Do not use for a final motion score of a finished page. Use Design-13 Quality Pack's motion check.
- Do not use for the library's own timing tokens. UI Library entries take their durations and curves from UI-25 Easing & Timing; follow UI-25 when the two disagree inside this library.

## Routing

| Job | Call | Why |
| --- | --- | --- |
| Animate something new | `motion-design` + the build tool (GSAP, Framer Motion, CSS) | Plans purpose, timing and easing before code |
| Fix motion that feels wrong | `motion-design` → "review this animation" | Names what is off and how to correct it |
| Brand motion rules | `motion-design` → "define a motion style for <brand>" | Turns a personality into timing and easing choices |

## Install

**Claude Code, Codex and other agents:**

```bash
npx skills add LottieFiles/motion-design-skill
```

**Claude app (no Terminal):** download the repo as a ZIP, zip only the `skills/motion-design` folder, upload it in Settings → Skills and switch it on.

No other requirements: it is guidance only and runs no scripts.

## How to ask

- "Use motion-design to plan the transitions for this onboarding flow, then build them in Framer Motion."
- "Review this hover animation with motion-design and tell me what makes it feel cheap."
- "Define a calm, premium motion style for my portfolio site."

## Watch-outs

- It sets the principles, not the code style. Pair it with a build skill such as Design-08 GSAP Skills.
- Keep motion short and respect reduced-motion settings; ask for both in the prompt.
- Do not load it alongside several other motion skills at once; one principles skill per session is enough.

## Credit

Original work by LottieFiles, MIT. Checked on 2026-11-17 at commit `f9a8a04`.

## Copy-ready English prompt

```text
Use the motion-design skill. Before writing code, tell me the purpose, the property that moves, the duration and the easing for each animation in <screen or component>. Then build it in <CSS / Framer Motion / GSAP> and respect prefers-reduced-motion.
```
