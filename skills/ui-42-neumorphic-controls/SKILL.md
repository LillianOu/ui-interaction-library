---
name: ui-42-neumorphic-controls
description: Use when a smart-home, wellness, audio, booking or shop interface should feel soft and tactile instead of flat; pick one of six neumorphic (soft UI, 新擬態) controls — light switch, thermostat dial, media player, file upload, booking picker, quantity stepper — each with a press-sink-and-spring-back interaction. Neumorphic Controls (新擬態元件六式) recipe with contrast, keyboard, touch and reduced-motion handling.
---
# UI-42 — 新擬態元件六式 / Neumorphic Controls

**Category:** 輸入與控制 / Inputs & Controls

## Effect

Every control looks moulded out of the same pale surface. Raised parts catch a soft highlight top-left and cast a soft shadow bottom-right; pressed or "on" parts sink into the surface with an inner shadow. When you press, the control sinks; when you let go, it springs back and the state changes, so each tap feels like a real button on a real object. A single muted accent colour per control carries the value (knob, arc, bars, selected day), so the state is never shown by shadow alone.

## When to use

Use for a small number of hero controls on a calm, light screen: a smart-home panel, a thermostat, a meditation or audio player, a booking widget, a product quantity. Pick the variant that matches the job; a screen can use several variants together as long as they share one surface colour. Do not use soft UI for dense forms, data tables or anything that needs high-contrast affordances everywhere. This skill is an interaction recipe, not an existing code component.

| No. | Term | 中文 | Interaction | Key spec |
| --- | --- | --- | --- | --- |
| 01 | Light Switch | 燈光開關 | Press: track sinks; release: knob slides and state flips | Inset pill track, raised round knob, knob tinted with the accent when on, status text "Ambient light · On/Off" |
| 02 | Thermostat Dial | 溫控旋鈕 | Drag the dial (or the linked slider); arc, indicator dot and number move together | Raised round dial with fine tick marks, accent progress arc around it, large number in the centre, range e.g. 16–30° |
| 03 | Media Player | 播放器 | Tap the raised play button to toggle; spectrum and progress run while playing, bars settle when paused | Raised circular play/pause button, row of accent spectrum bars above, inset progress track with time |
| 04 | File Upload | 文件上傳 | Press: button sinks; file cards gather into one, progress fills, check appears, then the panel resets | Inset drop well, raised upload button inside, thin inset progress bar, percentage text |
| 05 | Booking Picker | 預約組件 | Choose a day: it sinks and fills with the accent; time slots open below; choose a slot: the booking summary appears | Row of raised day tiles, selected tile inset or accent-filled, raised slot pills, selected slot inset |
| 06 | Quantity Stepper | 數量調節 | Tap − / +: the button sinks and springs back; count and subtotal update together; buttons disable at the limits | Two raised round buttons around a large accent number, subtotal line underneath |

## Interaction contract

- Input: mouse, touch, pen and keyboard for every variant. Press feedback starts on `pointerdown` (sink) and the state change commits on release (`click`), so a drag-off cancels the press.
- States: **default (raised)**, **hover** (slightly stronger highlight), **pressed (sunk)**, **focus-visible**, **on/selected (inset or accent)**, **disabled** (flat, no shadow, muted text), plus per variant: playing/paused (03), idle/uploading/done/cancelled (04), no-day/day-chosen/booked (05), at-min/at-max (06).
- 01 Light Switch: a `<button role="switch" aria-checked>` with a visible label; Space and Enter toggle. The knob position and the status text both change.
- 02 Thermostat Dial: the dial is `role="slider"` with `aria-valuemin/max/now` and `aria-valuetext="22 degrees"`. Drag by angle around the centre, clamp at the ends (no wrap from 30 to 16). Arrow keys ±1, Page Up/Down ±5, Home/End to the limits. A linked `<input type="range">` is optional but gives touch users a large target.
- 03 Media Player: play/pause is a `<button aria-pressed>` with the label "Play" or "Pause". Progress is a `role="progressbar"` or a seekable slider; time text updates once a second, not every frame, for screen readers.
- 04 File Upload: a real `<input type="file">` (or drop zone) behind the button. While uploading the button reads "Cancel" and Escape cancels. Progress is `role="progressbar"` with `aria-valuenow`; result ("Uploaded" / "Cancelled" / "Failed — retry") is announced in an `aria-live="polite"` region. The success state holds ~1.5 s before resetting.
- 05 Booking Picker: days are a `role="radiogroup"` (arrow keys move, Space selects); slots are a second radiogroup that only appears after a day is chosen. The booking summary is announced. Past or full days are disabled, not hidden.
- 06 Quantity Stepper: two `<button>`s labelled "Decrease quantity" / "Increase quantity"; the value is in an `<output>` with `aria-live="polite"`. Clamp to min/max and set `disabled` on the button at each limit. Optionally allow typing the value.
- Edge cases: interrupted presses (pointer cancel, scroll start, leaving the window) release the sink without changing state; rapid taps queue no more than one state change per release; resize keeps the dial's angle maths based on its live centre; long labels wrap below the control rather than shrinking it.
- Accessibility: soft UI is low-contrast by nature, so do not rely on shadow to show state. Text and icons need 4.5:1 against the surface, the control's outline (shadow pair or a hairline border) needs about 3:1, focus needs a clear visible ring (not just a deeper shadow), and every on/selected state also changes colour, position or text. Hit areas at least 44 × 44 px.
- Reduced motion: keep the sink and the state change, drop the travel. The knob jumps instead of sliding, the spectrum bars stop animating and show a static level, the upload goes straight to its progress values without the card gathering, and slots appear without the height animation.

## Implementation notes

- Surface tokens: one surface colour plus a light and a dark shadow made from it, for example `--nm-bg:#E7ECF2; --nm-hi:#FFFFFF; --nm-lo:#A9B6C7`. Raised: `box-shadow: 8px 8px 18px var(--nm-lo), -8px -8px 18px var(--nm-hi)`. Inset: the same pair with `inset`. Small parts use smaller offsets (3–4px) so depth scales with size.
- The page background must equal `--nm-bg`; a control on a different colour breaks the illusion.
- Dark theme: darker surface (`#20252C`), shadow pair `#14181D` / `#2C333C`, and reduce shadow strength — soft UI in dark mode reads as mud if the offsets stay large.
- Press: on `pointerdown` swap to the inset shadow and `transform: scale(.97)`; on release return with a spring curve (`cubic-bezier(.34,1.56,.64,1)`, 220–320 ms, see UI-25 and UI-26). Use `setPointerCapture` for the dial drag.
- 01: animate the knob with `transform: translateX()`; the track stays inset at all times, the knob gets the accent fill when on.
- 02: an SVG circle arc with `stroke-dasharray` / `stroke-dashoffset` driven by the value; angle from `Math.atan2` around the dial centre, mapped to a 270° sweep. Ticks are short SVG lines.
- 03: bars are CSS `scaleY` animations with staggered `animation-delay`; set `animation-play-state` from the playing state, and transition them to a low resting height when paused. Drive progress with `requestAnimationFrame` and stop the loop on pause or when off screen.
- 04: three small file cards absolutely positioned, then translated into one stack with a short stagger (UI-27); progress width animates from the real upload `progress` event, or a timer in demos.
- 05: open the slot row with `grid-template-rows: 0fr → 1fr` so the card grows smoothly; the selected day uses the accent fill plus inset shadow.
- 06: keep price and quantity in state and render the subtotal from them; format with `Intl.NumberFormat`.
- Colour: one accent per control, muted and mid-tone (sage, lavender, copper, teal, rose). Accent text is only for large numbers; small labels stay in the ink colour for contrast.
- Avoid: neumorphism on every element of a page, grey text on grey surface, shadow as the only state cue, hover-only affordances, animating `box-shadow` on many elements every frame (switch classes instead), and dial maths based on stale cached positions.

## Prompt terms

Name the term in the prompt; "neumorphic" or "soft UI" is what steers the AI tool to the moulded look. Short prompts written for this library:

| No. | English prompt line | 中文提示詞 |
| --- | --- | --- |
| 01 | Design a light neumorphic light switch: an inset pill track and a raised round knob shaped by soft highlights and shadows. On press the track sinks; on release the knob slides across, springs back and the light state flips. | 設計淺色新擬態燈光開關：內凹膠囊軌道配凸起圓形滑塊，用柔和高光和陰影塑造質感。按下時軌道下沉，鬆開後滑塊平移、回彈並切換燈光狀態。 |
| 02 | Design a neumorphic thermostat dial with soft shadows and fine tick marks. While dragging, the indicator dot, the progress arc and the temperature number all move together. | 設計新擬態溫控旋鈕，加入柔和陰影和細小刻度。拖動時，指示點、進度圓弧和溫度數字同步變化。 |
| 03 | Design a light neumorphic media player with a raised play button. Tapping toggles play and pause; while playing the spectrum bars and progress bar move, and when paused the bars settle down. | 設計淺色新擬態播放器，使用凸起的播放按鈕。點擊切換播放與暫停，播放時頻譜和進度條動態變化，暫停時頻譜收回。 |
| 04 | Design a neumorphic upload panel with an inset drop well. After the button is pressed the file cards gather into one, the progress bar fills, a check mark appears, then the panel springs back to its start. | 設計帶內凹入口的新擬態上傳組件。按下按鈕後文件卡片依次收攏，進度條展開填充；完成後顯示勾選，再回彈復位。 |
| 05 | Design a light neumorphic booking picker that uses soft shadows to show the selected state. Choosing a day opens the time slots below; choosing a slot shows the booking result, and the layout grows and shrinks smoothly. | 設計淺色新擬態預約組件，用柔和陰影區分選中狀態。選擇日期後展開時段，選中時段後顯示預約結果，佈局流暢伸縮。 |
| 06 | Design a neumorphic quantity stepper with raised minus and plus buttons. Each tap sinks the button and springs it back, the quantity and price update together, and the button at a limit is disabled. | 設計新擬態數量調節組件，使用凸起的加減按鈕。點擊時按鈕下沉回彈，數量與金額同步變化，到達邊界時禁用對應按鈕。 |

## Acceptance criteria

1. The chosen variant matches its key spec above, on a surface whose page background equals the control surface.
2. Press sinks on pointer down and commits on release; dragging off or pointer cancel releases without a state change.
3. Every state is shown by colour, position or text as well as shadow; text meets 4.5:1 and focus rings are clearly visible in light and dark themes.
4. All six variants work fully with keyboard (Space/Enter, arrows, Home/End where relevant, Escape cancels upload) and expose correct roles and live announcements.
5. The dial clamps at its limits, the stepper disables at its limits, and the upload can be cancelled.
6. Reduced-motion mode keeps the information and the sink feedback without slides, spectrum loops or height animation.
7. Responsive at 375px, 768px and 1440px; no console errors; animation frames and listeners stop when paused, cancelled or off screen.

## Copy-ready English prompt

```text
Build a reusable set of light neumorphic (soft UI) controls that share one surface colour, selected by a `variant` prop: "switch", "dial", "player", "upload", "booking" and "stepper".
- Surface: page and controls use the same pale surface; raised parts have a light shadow top-left and a darker shadow bottom-right, sunk parts use the same pair inset. One muted accent colour per control carries the value. Define surface, highlight, shadow and accent as CSS tokens with a dark-theme set.
- Press feel: on pointer down the control sinks (inset shadow, scale .97); on release it springs back (cubic-bezier(.34,1.56,.64,1), ~260ms) and the state changes. Pointer cancel releases without changing state.
- switch: button role="switch" with an inset pill track and a raised round knob that slides and takes the accent fill when on; status text "On/Off".
- dial: role="slider" thermostat (16–30°) with fine ticks, an accent SVG progress arc, a centre number and an indicator dot, all updated together while dragging by angle; arrows ±1, PageUp/Down ±5, Home/End; clamps at the ends.
- player: raised round play/pause button (aria-pressed), accent spectrum bars that animate while playing and settle when paused, inset progress track with elapsed/total time.
- upload: inset drop well around a raised button backed by a real file input; on start, three file cards gather into one, an inset progress bar fills with a percentage, a check shows on success, then it resets; the button becomes Cancel while running and Escape cancels; results go to an aria-live region.
- booking: radiogroup of raised day tiles; the chosen day sinks and fills with the accent; a slot radiogroup opens below with a smooth height change; choosing a slot shows and announces the booking summary; past days are disabled.
- stepper: raised − and + buttons around a large accent number in an <output>, subtotal updates with the quantity, buttons disable at min and max.
Accessibility: 4.5:1 text contrast, a clearly visible focus ring, state never shown by shadow alone, 44px hit areas. Reduced motion: keep the sink and the state change but remove slides, loops and height animation. Responsive at 375, 768 and 1440px. Clean up listeners and animation frames.
```
