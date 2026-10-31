---
name: 56-typewriter
description: Use when an AI assistant, search box or hero tagline should type its text out character by character with a caret, optionally cycling through phrases. Typewriter (打字機) recipe with typing speed, pause control, screen readers and reduced-motion handling.
---
# 56 — 打字機 / Typewriter

**Category:** 文字動效 / Text & Type

## Effect

The text appears one character at a time with a blinking caret, as if someone is typing it live. In a loop, it pauses, deletes and types the next phrase.

## When to use

Use for AI assistant intros, search placeholders that suggest queries, and hero taglines that rotate through a few phrases. Not for content people must read in full, error messages, or more than about four phrases. This skill is an interaction recipe, not an existing code component.

Part of the sixteen-effect motion set (45–60), inspired by the Douyin video 「非程序员AI开发必看教程：16种常见动画效果科普」 by 大锤和AI. Specs, prompts and demo are written for this library. Timing and easing follow 45 Easing & Timing.

## Interaction contract

- Input: starts when visible; a pause control stops the loop (it runs longer than 5 seconds).
- States: typing, holding, deleting, paused, done (if not looping).
- Cancellation and edge cases: pauses when off screen or the tab is hidden and resumes where it left off; reserve height so a longer phrase doesn't push content down; emoji and CJK characters are counted as whole characters.
- Accessibility: screen readers get the full text once (a visually hidden copy listing all phrases) and the animated text is `aria-hidden`; no `aria-live` on the typing element.
- Reduced motion: show the complete phrase without typing; optionally swap phrases every few seconds; caret does not blink.

## Implementation notes

- Timers: type 40–70ms per character, hold 1.2–2s, delete 20–35ms per character, 300ms gap before the next phrase.
- Use `Array.from(text)` or `Intl.Segmenter` so multi-byte characters aren't split.
- Caret: an inline element with `animation: blink 1s steps(1) infinite`.
- Stop timers with `IntersectionObserver` and `visibilitychange`; clear them on unmount.
- Avoid: typing very long sentences, random delays that feel broken, and moving layout as lines wrap.

## Acceptance criteria

1. Text types at 40–70ms per character with a caret, holds, deletes and moves to the next phrase.
2. A pause control stops it; it also pauses off screen and in hidden tabs.
3. Screen readers get the full text once; layout doesn't jump.
4. Works with mouse, touch and keyboard as described in the interaction contract.
5. Reduced-motion mode presents the same information without the movement described above.
6. Only `transform`, `opacity`, `filter`, colour and shadow animate; no layout thrash; smooth on a mid-range phone.
7. No console errors or leaks; listeners, observers, timers and animation frames are cleaned up.
8. Responsive at 375px, 768px and 1440px.

## Prompt terms

| English prompt line | 中文提示詞 |
| --- | --- |
| Add a Typewriter effect to the assistant headline: type each phrase character by character with a blinking caret, pause, delete, then type the next. | AI 助手標題加打字機效果（Typewriter）：文字一個字一個字打出來，帶閃爍游標，停頓後刪除再打下一句。 |

## Copy-ready English prompt

```text
Add a typewriter effect to this headline. Cycle through 3 phrases: type at 55ms per character (use Array.from for multi-byte characters), hold 1.4s, delete at 25ms per character, wait 350ms, then type the next. Show a 2px caret blinking with steps(1). Reserve the height of the longest phrase. Pause when off screen (IntersectionObserver) or when the tab is hidden, and add a Pause/Play button. Put all phrases in a visually hidden span for screen readers and mark the animated text aria-hidden. Under prefers-reduced-motion show the full phrase with a static caret.
```
