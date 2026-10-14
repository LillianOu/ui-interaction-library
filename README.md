# UI Interaction Library

A private, evolving reference library of reusable UI interaction patterns for product and interface design. It records interaction intent, behaviour, accessibility considerations, and copy-ready implementation prompts in English and Traditional Chinese.

This is a working library, not a public portfolio, demo site, component package, or finished Codex skill. The cursor-driven animated hero will be added later as another numbered pattern in this library.

## Current contents

Eight documented patterns live in [`patterns/`](patterns/). New work continues at **09**.

- [Pattern index](patterns/README.md)
- [How to update](CONTRIBUTING.md)
- [Changelog](CHANGELOG.md)
- [Licence decision](LICENSE-DECISION.md)

Five motion skill specifications live in [`skills/`](skills/), one folder per skill with a `SKILL.md`, usable by Claude Code (`.claude/skills/`) and Codex (`.agents/skills/`):

- `cursor-luminous-flow` — Cursor-driven Luminous Flow
- `scroll-helix-flow` — Scroll-driven Helix Flow
- `immersive-float` — Immersive Float
- `scroll-vortex-transit` — Scroll-driven Vortex Transit
- `hover-door-bloom` — Hover-triggered Door Bloom

## Working principles

- Describe reusable behaviours, not a single product scenario.
- Include pointer, touch, keyboard, accessibility, reduced-motion, cancellation, state, and implementation safeguards where relevant.
- Keep every entry editable and independently useful.
- Do not describe unfinished work as production-complete.
