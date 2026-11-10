---
name: music-02-suno-style-prompt
description: "Use when a Suno Style (Music Style) prompt is needed; builds genre blend, BPM and groove, instruments, vocal, mood, exclusions and A/B variants."
---

# Music-02 — 曲風提示詞 / Suno Style Prompt

**Category:** 工具庫 / Tool Library · 音樂 / Music

Writes the text for Suno's Style field, plus Exclude Styles and A/B variants. Covers genre blending, rhythm, vocal, mood and scoring for video. Write the prompt in **English** (Suno reads it best), even for Mandarin songs, and name the language ("Mandarin vocals").

## Order (most important first)

1. **Genre anchor** plus 1–2 modifiers. One main genre; the rest add flavour. e.g. `Mandarin R&B ballad, C-pop, lo-fi soul`
2. **Groove:** BPM, feel (laid-back, swung, half-time), drums.
3. **Instruments (3–5 max):** e.g. Rhodes, warm sub bass, soft trap hi-hats, nylon guitar, string swell.
4. **Vocal:** gender, texture (breathy, airy, husky), technique (falsetto, runs, harmonies), duet if wanted.
5. **Mood arc:** e.g. `nostalgic verses, warm uplifting chorus`.
6. **Production:** e.g. `intimate, polished modern mix, catchy repetitive hook`.

## Rules

- About 150–250 characters, comma-separated descriptors, no sentences.
- Never use artist names. Describe the sound instead.
- Suno ignores duration instructions; length comes from how much lyric there is.
- Always give an Exclude Styles line, e.g. `rap, EDM drop, heavy distortion`.
- Music for video or games: describe the scene, pacing and emotion, and turn Instrumental on.
- Cover or remix: keep the melody; change only the genre, groove and instrument lines.
- Separating vocals and instruments is Suno's own Stems feature; no prompt needed.

## Output

1. Style prompt (code block)
2. Exclude Styles (code block)
3. Two variants for A/B runs, e.g. softer acoustic and duet
4. Tip: generate the same prompt 4–6 times and keep the take with the strongest chorus
