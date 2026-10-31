---
name: 45-motion-essentials
description: Use when a page, landing page, pricing table, dashboard or product UI needs motion and you want to name the exact effect instead of asking for "some animation"; pick from sixteen named effects (Border Beam, Spotlight, Tilt, Scroll Storytelling, Scramble Text, Parallax, Magnetic, Typewriter, Marquee, Shimmer, Count Up, Scroll Reveal, Spring, Stagger, Hover Lift, Easing) with timing rules, prompt terms in English and Chinese, and touch, keyboard and reduced-motion handling.
---
# 45 — 常用動效十六式 / 16 Essential Motion Effects

**Category:** 動態視覺效果 / Motion Effects

## Effect

A vocabulary of the sixteen motion effects that appear on most modern product sites, each with a name, a job, a spec and a prompt line. Knowing the term is what gets an AI tool to build the effect you mean: "make it feel premium" gets you random fades; "add a Border Beam to the recommended plan" gets you exactly that. The last section gives the timing and easing rules that make any of them feel right.

## When to use

Use when you are designing or prompting a page and want motion with a purpose: to point at one thing, to explain a product while scrolling, to show that something is loading, or to make a control feel physical. Pick the effect by its job in the table, then use its prompt line. Use two or three per page, not sixteen. This skill is an interaction recipe, not an existing code component.

Concept inspired by the Douyin video 「非程序员AI开发必看教程：16种常见动画效果科普」 by 大锤和AI. Descriptions, specs, prompts and the demo are written for this library.

## The sixteen effects

| No. | Term | 中文 | Trigger | Job: use it to… | Key spec |
| --- | --- | --- | --- | --- | --- |
| 01 | Border Beam | 邊緣流光 | Ambient loop | Point at the one recommended plan, new feature or primary card | A short bright arc travels around the border; 1–2px; one loop every 3–4s, linear; only one element per screen |
| 02 | Spotlight | 聚光 | Pointer move | Make a grid of feature cards feel alive and show which one you're on | Soft radial glow (~200–300px) follows the pointer inside each card, and lights the border nearest the pointer |
| 03 | Tilt | 3D 傾斜 | Pointer move / drag | Show off a single physical-looking object: membership card, product, ticket | Card rotates toward the pointer, max 8–12°, `perspective` ~800px, a moving glare; springs flat on leave |
| 04 | Scroll Storytelling | 滾動敘事 | Scroll | Explain a product one feature at a time | Visual stays pinned (sticky) while text steps scroll past; the active step highlights and the visual swaps state |
| 05 | Scramble Text | 亂碼解碼 | In view / hover | Tech, AI, security or launch headlines | Characters cycle through random glyphs, then lock left to right; 0.8–1.5s total; monospace or tabular font |
| 06 | Parallax | 視差滾動 | Scroll | Give a hero depth with layered art | Background layers move slower than the page (factor 0.2–0.6), foreground at normal speed; subtle, never seasick |
| 07 | Magnetic | 磁吸 | Pointer near | Pull attention to one primary call-to-action | Button drifts 20–35% of the pointer offset within ~100px radius; label moves a little more; springs back |
| 08 | Typewriter | 打字機 | In view / loop | AI assistants, search boxes, hero taglines | Text appears one character at a time (40–70ms/char) with a caret; hold, delete, next phrase |
| 09 | Marquee | 跑馬燈 | Ambient loop | Logo walls, testimonials, "trusted by" strips | Rows scroll endlessly (rows in opposite directions), edge fade, pauses on hover/focus, has a pause control |
| 10 | Shimmer | 流光 | Loading / ambient | Skeleton loading states; a sheen across a promo button | A light band sweeps across a surface; ~1.2–1.6s per pass on skeletons; occasional sweep on buttons |
| 11 | Count Up | 數字滾動 | In view | Stats, KPIs, dashboards, social proof | Number runs from 0 to its value in 1–1.6s with ease-out; tabular figures so width doesn't jump |
| 12 | Scroll Reveal | 滾動出現 | In view | Lists, articles, feature sections | Each block fades and rises 16–24px as it enters; 400–600ms ease-out; plays once |
| 13 | Spring | 彈性 | Any state change | Likes, toggles, sliders, playful moments | Motion overshoots slightly and settles, like a real object; use spring physics, not a fixed curve |
| 14 | Stagger | 錯峰 | With any group entrance | Grids, menus, list items entering together | Items start one after another, 40–80ms apart; total sequence under ~500ms |
| 15 | Hover Lift | 懸停上浮 | Hover / focus | Product cards and clickable tiles | Card rises 4–8px and its shadow grows; 150–200ms ease-out; pressed state settles back down |
| 16 | Easing | 緩動 | Every animation | The rule behind all of the above: how speed changes over time | Enter = ease-out, exit = ease-in, move = ease-in-out, loops = linear; never linear for UI moving between places |

## Timing and easing rules

| Size of change | Examples | Duration | Easing |
| --- | --- | --- | --- |
| Micro | Hover, press, toggle, checkbox | 100–200ms | ease-out |
| Small | Tooltip, dropdown, toast | 150–250ms | ease-out in, ease-in out |
| Medium | Panel, modal, card expand, reveal | 250–400ms | ease-out, or spring |
| Large | Page transition, hero entrance | 400–700ms | ease-in-out, or spring |
| Ambient loop | Beam, marquee, shimmer | 1.2–30s per cycle | linear, always pausable |

- Exits run about 25% faster than entrances.
- Stagger step 40–80ms; keep the whole sequence under ~500ms so the last item isn't late.
- One hero effect per screen. Effects that loop forever (01, 08, 09, 10) need a reason to exist and a way to stop.
- Good default curves: ease-out `cubic-bezier(.2,.8,.2,1)`, ease-in `cubic-bezier(.4,0,1,1)`, ease-in-out `cubic-bezier(.65,0,.35,1)`; spring via CSS `linear()` generated from stiffness ~170 / damping ~14, or Framer Motion / Motion One `type: "spring"`.

## Interaction contract

- Input: every pointer-driven effect (02, 03, 07, 15) also works without a mouse. Keyboard focus places the spotlight on the focused card (02), tilts with arrow keys or shows a resting angle (03), and lifts the focused card (15). On touch, 03 follows a drag; 02 and 07 are skipped or reduced to a press state, because there is no hover.
- States: idle, hover, focus-visible, pressed, playing, paused, finished. Scroll-triggered effects (04, 11, 12) play once by default; a replay is optional.
- Content is never hidden behind the animation: 05 and 08 expose the final text to assistive technology (`aria-label` on the element, animated glyphs `aria-hidden`); 11 exposes the final number; 12 content is readable if JavaScript fails (start visible, add the hidden state only once the script runs).
- Cancellation and edge cases: interrupting an animation (hover out mid-lift, a second click mid-spring) continues from the current value instead of jumping. Pointer leave and `pointercancel` reset 02, 03 and 07. Loops pause when the tab is hidden or the element is off screen. Resizing re-measures distances for 06, 07 and 13.
- Accessibility: anything that moves for more than 5 seconds (01, 08, 09, 10) has a pause/stop control or stops on its own (WCAG 2.2.2). Marquee duplicates are `aria-hidden`; the list is readable once. Scroll regions used for 04 are focusable and labelled. No flashing more than three times a second.
- Reduced motion (`prefers-reduced-motion: reduce`): 01 static gradient border; 02 static glow on hover/focus; 03 flat card; 04 steps swap without a pinned scrub; 05 and 08 show final text; 06 layers still; 07 no movement; 09 a static, scrollable row; 10 a static skeleton; 11 the final number; 12 everything visible; 13, 14, 16 instant state change or short opacity fade; 15 shadow change only, no rise.

## Implementation notes

- 01: a `::before` ring with `conic-gradient(from var(--angle), transparent 0 70%, accent 80%, transparent 95%)`, masked to the border with `mask-composite: exclude`, and `--angle` registered with `@property` so it animates.
- 02: one `pointermove` on the grid writes `--x`/`--y` per card (`clientX - rect.left`); each card paints `radial-gradient(250px circle at var(--x) var(--y), …)` on its background and on a masked border layer.
- 03: `rotateX(-py * max) rotateY(px * max)` from the pointer position in [-0.5, 0.5]; update in `requestAnimationFrame`; glare is a radial gradient on `::after` positioned by the same values.
- 04: `position: sticky` visual beside the steps, `IntersectionObserver` (threshold ~0.6) marks the active step. For scrubbed animation, GSAP ScrollTrigger (see 32 Swift Swallow) or CSS `animation-timeline: view()`.
- 05 and 08: a `requestAnimationFrame` loop or timers that stop when the element leaves the viewport; reserve the final text width up front so layout never jumps.
- 06: `transform: translate3d(0, scrollY * factor, 0)` per layer in one `rAF`-throttled scroll handler, or CSS `animation-timeline: scroll()`; never animate `background-position` on scroll.
- 07: translate toward the pointer only within a radius; spring back with a transition; `(hover: hover) and (pointer: fine)` only.
- 09: duplicate the track once, animate `translateX(0 → -50%)` linearly, `mask-image` fade at the edges, `animation-play-state: paused` on hover, focus and a pause button.
- 10: `linear-gradient(90deg, base, highlight, base)` at `background-size: 200%`, animating `background-position`; set `aria-busy="true"` on the loading region.
- 11: `requestAnimationFrame` with ease-out-expo, `Intl.NumberFormat` for separators, `font-variant-numeric: tabular-nums`.
- 12 and 14: `IntersectionObserver` toggles a class; stagger with `transition-delay: calc(var(--i) * 60ms)`.
- 13: CSS `linear()` spring easing (with a `cubic-bezier(.34,1.56,.64,1)` fallback), the Web Animations API, or Motion / Framer Motion springs.
- 15: animate only `transform` and `box-shadow` (or the opacity of a pre-rendered shadow layer) for smooth frames.
- Libraries are optional: every effect is achievable with CSS plus a little JavaScript. Use GSAP (32 Swift Swallow) for timelines and scroll scrubbing, Motion / Framer Motion for springs and layout in React.
- Avoid: animating `width`, `height`, `top` or `left` on every frame; scroll handlers without `rAF`; several looping effects on one screen; effects that delay reading or clicking; motion with no job.

## Prompt terms

Name the effect in the prompt; the term is what steers the AI tool.

| No. | English prompt line | 中文提示詞 |
| --- | --- | --- |
| 01 | Add a Border Beam to the recommended plan card: a short bright arc travelling around its 1.5px border every 3.5 seconds; no other card gets it. | 給推薦套餐卡片加邊緣流光（Border Beam）：一小段亮光沿 1.5px 邊框循環流動，3.5 秒一圈，其他卡片不加。 |
| 02 | Add a Spotlight to the feature cards: a soft radial glow follows the cursor inside each card and lights the nearest border; on keyboard focus the glow sits in the centre. | 功能卡片加聚光效果（Spotlight）：滑鼠在卡片上移動時，柔和光暈跟隨游標並照亮附近邊框；鍵盤聚焦時光暈置中。 |
| 03 | Make the membership card Tilt in 3D toward the cursor, max 10 degrees, with a moving glare; it springs back flat when the cursor leaves. | 會員卡做 3D 傾斜（Tilt）：跟著游標方向傾斜，最多 10 度，帶反光；游標離開時彈回平放。 |
| 04 | Build a Scroll Storytelling section: the product image stays pinned on the right while three feature steps scroll on the left; the active step highlights and the image changes to match. | 做一段滾動敘事（Scroll Storytelling）：右邊產品圖固定不動，左邊三個賣點依次滾過，當前賣點高亮，圖片跟著切換。 |
| 05 | Give the headline a Scramble Text entrance: characters cycle through random glyphs and lock in from left to right over about one second when it enters the screen. | 標題加亂碼解碼（Scramble Text）：進入畫面時字元先亂跳，約一秒內從左到右逐個定格成正確文字。 |
| 06 | Add Parallax to the hero: sky, far mountains and near trees move at different speeds as the page scrolls, background slowest. | 首屏加視差滾動（Parallax）：天空、遠山、近樹隨頁面滾動以不同速度移動，背景最慢。 |
| 07 | Make the main call-to-action Magnetic: when the cursor comes within 100px the button drifts toward it, and springs back when the cursor leaves. Desktop only. | 主按鈕加磁吸效果（Magnetic）：游標靠近 100px 內時按鈕被吸過去，離開時彈回原位，只在桌面端。 |
| 08 | Add a Typewriter effect to the assistant headline: type each phrase character by character with a blinking caret, pause, delete, then type the next. | AI 助手標題加打字機效果（Typewriter）：文字一個字一個字打出來，帶閃爍游標，停頓後刪除再打下一句。 |
| 09 | Add a Marquee of customer logos and quotes: two rows scrolling endlessly in opposite directions, fading at the edges, pausing on hover, with a pause button. | 加一條跑馬燈（Marquee）：客戶標誌和評價兩排反向無限循環滾動，兩端漸隱，懸停暫停，並提供暫停按鈕。 |
| 10 | Show a Shimmer skeleton while the card loads, and add an occasional Shimmer sheen across the promo button. | 卡片載入時顯示帶流光（Shimmer）的骨架屏，促銷按鈕偶爾掃過一道流光。 |
| 11 | Make the stats Count Up from zero to their values over 1.4 seconds with ease-out when they scroll into view, using tabular numbers. | 數據做數字滾動（Count Up）：進入畫面時從零滾到目標值，1.4 秒，減速收尾，數字等寬。 |
| 12 | Add Scroll Reveal to the article list: each card fades in and rises 20px as it enters the viewport, once only. | 文章列表加滾動出現（Scroll Reveal）：每張卡片進入視窗時淡入並上移 20px，只播一次。 |
| 13 | Use Spring motion for the like button and the slider handle: a small overshoot that settles, instead of a plain ease-out. | 點讚按鈕和滑桿用彈性動效（Spring）：輕微超出再回彈定位，不要普通的減速。 |
| 14 | Stagger the grid entrance: cards appear one after another 60ms apart instead of all at once. | 網格入場用錯峰（Stagger）：卡片間隔 60 毫秒依次出現，不要同時出現。 |
| 15 | Add Hover Lift to the product cards: on hover or focus the card rises 6px and its shadow deepens in 180ms; pressing settles it back. | 商品卡片加懸停上浮（Hover Lift）：滑鼠移上或聚焦時上浮 6px、陰影加深，180 毫秒；按下時回落。 |
| 16 | Apply proper Easing everywhere: ease-out for things entering, ease-in for things leaving, ease-in-out for things moving between places, linear only for loops; micro-interactions 100–200ms. | 全站統一緩動（Easing）：進場用減速，離場用加速，位移用先加速後減速，只有循環動畫用勻速；小動作 0.1–0.2 秒。 |

## Acceptance criteria

1. Each effect used matches its key spec and does the job named for it; no more than one ambient loop (01, 09, 10) is visible in a viewport at once.
2. Durations and easing follow the timing table; exits are faster than entrances.
3. Pointer effects have a keyboard equivalent or a resting state on focus, and touch either follows a drag or falls back to a press state.
4. Final text and numbers (05, 08, 11) are exposed to screen readers; marquee duplicates are hidden from them; content is visible without JavaScript.
5. Every effect that runs longer than 5 seconds can be paused; loops pause off screen and in hidden tabs.
6. Reduced-motion mode presents the same information with the fallbacks listed above.
7. Only `transform`, `opacity`, `filter`, colours and shadows animate; no layout thrash, steady 60fps on a mid-range phone; listeners, observers and animation frames are cleaned up.
8. Responsive at 375px, 768px and 1440px.

## Copy-ready English prompt

```text
Add purposeful motion to this page using named effects. For each section, pick at most one effect from this list and implement it as specified:
- Border Beam on the single recommended card: a short bright arc travelling around a 1.5px border every 3.5s (conic-gradient + @property angle + mask).
- Spotlight on feature cards: radial glow follows the pointer inside each card via --x/--y; centred on keyboard focus.
- Tilt on one hero object: up to 10° toward the pointer with perspective 800px and a moving glare; springs flat on leave; drag on touch.
- Scroll Storytelling: sticky visual, steps scroll past, IntersectionObserver marks the active step and swaps the visual.
- Scramble Text on a headline: glyphs cycle then lock left to right in ~1s; aria-label holds the final text.
- Parallax on layered hero art: layers translate at factors 0.2–0.6 in one rAF-throttled scroll handler.
- Magnetic on the primary CTA: drifts ~30% toward the pointer within 100px, springs back; fine pointers only.
- Typewriter on a tagline: 50ms per character, caret, hold, delete, next phrase; full text available to screen readers.
- Marquee for logos/testimonials: duplicated track, translateX(0 → -50%) linear, edge fade, pause on hover/focus and a pause button.
- Shimmer on loading skeletons (aria-busy) and an occasional sheen on a promo button.
- Count Up on stats: 0 → value in 1.4s ease-out-expo, tabular numbers, final value exposed to screen readers.
- Scroll Reveal on lists: fade + rise 20px once on entry; content visible if JS fails.
- Spring for likes, toggles and sliders: slight overshoot via CSS linear() spring easing or a spring library.
- Stagger group entrances: 40–80ms apart, whole sequence under 500ms.
- Hover Lift on clickable cards: rise 6px, deeper shadow, 180ms ease-out; pressed settles back.
Timing: micro 100–200ms, small 150–250ms, medium 250–400ms, large 400–700ms; enter ease-out, exit ease-in and ~25% faster, move ease-in-out, loops linear.
Animate only transform, opacity, filter, colour and shadow. Pause loops off screen and in hidden tabs. Every loop longer than 5s needs a pause control. Respect prefers-reduced-motion: static border, static glow, flat card, final text and numbers, visible content, instant state changes. Make it work with mouse, touch and keyboard, responsive at 375px, 768px and 1440px, with no console errors and all listeners and observers cleaned up.
```
