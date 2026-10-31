---
name: 55-scramble-text
description: Use when a tech, AI, security or launch headline should decode into place, with characters cycling through random glyphs and locking in from left to right. Scramble Text (亂碼解碼) recipe with timing, layout stability, screen readers and reduced-motion handling.
---
# 55 — 亂碼解碼 / Scramble Text

**Category:** 文字動效 / Text & Type

## Effect

The text first appears as a jumble of random characters that keep changing, then locks into the real words letter by letter from left to right, like a message being decoded.

## When to use

Use for short headlines, labels and numbers on tech, AI, security, gaming or launch pages. Not for body text, long headlines (over ~25 characters) or text people must read quickly. This skill is an interaction recipe, not an existing code component.

Part of the sixteen-effect motion set (45–60), inspired by the Douyin video 「非程序员AI开发必看教程：16种常见动画效果科普」 by 大锤和AI. Specs, prompts and demo are written for this library. Timing and easing follow 45 Easing & Timing.

## Interaction contract

- Input: plays when the text enters the viewport (once), optionally on hover and on a replay control.
- States: idle (final text), scrambling, done.
- Cancellation and edge cases: retriggering mid-scramble restarts cleanly without leaving garbage; spaces and punctuation stay fixed; leaving the viewport mid-way finishes or stops at the final text.
- Accessibility: screen readers get the final text only (`aria-label` on the element and the animated glyphs `aria-hidden`, or a visually hidden copy).
- Reduced motion: final text shown immediately.

## Implementation notes

- Plan a reveal time per character (index ÷ length × ~0.7 of the duration, plus a little randomness); each frame, characters before their time show a random glyph, after it the real one. Total 0.8–1.5s.
- Run in `requestAnimationFrame`; stop and cancel the frame when done.
- Use a monospace font or `font-variant-numeric: tabular-nums` and reserve the final width so the layout doesn't jump.
- Glyph set: uppercase letters, digits and a few symbols (`!<>-_/[]{}=+*^?#`); escape `<` and `>` if using innerHTML.
- Avoid: scrambling paragraphs, looping forever, and text that changes size while scrambling.

## Acceptance criteria

1. Characters cycle then lock in left to right within 0.8–1.5s; layout width doesn't jump.
2. Screen readers announce only the final text.
3. Retriggering restarts cleanly.
4. Works with mouse, touch and keyboard as described in the interaction contract.
5. Reduced-motion mode presents the same information without the movement described above.
6. Only `transform`, `opacity`, `filter`, colour and shadow animate; no layout thrash; smooth on a mid-range phone.
7. No console errors or leaks; listeners, observers, timers and animation frames are cleaned up.
8. Responsive at 375px, 768px and 1440px.

## Prompt terms

| English prompt line | 中文提示詞 |
| --- | --- |
| Give the headline a Scramble Text entrance: characters cycle through random glyphs and lock in from left to right over about one second when it enters the screen. | 標題加亂碼解碼（Scramble Text）：進入畫面時字元先亂跳，約一秒內從左到右逐個定格成正確文字。 |

## Copy-ready English prompt

```text
Add a scramble-text entrance to this headline. When it enters the viewport (once, via IntersectionObserver), run a requestAnimationFrame loop for about 1.2s: each character has a reveal time of (index / length) × 0.7 × duration plus up to 120ms random; before that it shows a random glyph from A–Z, 0–9 and !<>-_/[]{}=+*^?#, after it the real character. Keep spaces and punctuation fixed, use a monospace or tabular font and reserve the width. Put the final text in aria-label and mark the animated characters aria-hidden. Replaying restarts cleanly. Under prefers-reduced-motion show the final text at once.
```
