---
name: music-01-suno-lyric-weaver
description: "Use when Lillian asks for song lyrics for Suno, especially Mandarin songs; writes rhymed, hook-first lyrics with Suno section tags."
---

# Music-01 — 歌詞編織 / Suno Lyric Weaver

**Category:** 工具庫 / Tool Library · 音樂 / Music

Writes lyrics ready to paste into Suno's Lyrics field. Built for Mandarin (also works in English): strict end rhyme, a hook that repeats early and often, concrete images, Suno section tags. Pair it with Music-02 for the Style prompt.

## Inputs (assume sensible defaults if missing)

- Theme and emotional arc, e.g. looking back at the past, grateful for now
- Language, genre, point of view (我 / 你 / 我們)
- Platform. Douyin / TikTok means hook-first and about 2:30–3:00 long

## Process

1. **Emotion first.** Write one sentence that states what the song feels.
2. **Hook first.** Write the chorus before the verses. Hook phrase is 4–7 characters of plain spoken words, sung on the first and last line of the chorus, heard 2–3 times inside 30 seconds.
3. **Rhyme plan (Mandarin).** One rhyme final (韻腳) per section, on every line end:
   - Verse: e.g. -ian / -ie (天 邊 年 面)
   - Pre-chorus: change rhyme to lift (e.g. -ou: 手 柔 走)
   - Chorus: an open vowel that is easy to sing (-ai: 在 來 愛, or -ang: 方 光)
   - Bridge: a new rhyme for contrast
   Check the pinyin final of every line end before delivering.
4. **Concrete images.** Verses use real objects and places (舊照片, 末班地鐵, 一副耳機), not abstract clichés.
5. **Structure:** `[Intro] [Verse 1] [Pre-Chorus] [Chorus] [Verse 2] [Pre-Chorus] [Chorus] [Bridge] [Final Chorus] [Outro] [End]`
6. **Suno formatting.** Section tags in English square brackets. Performance cues allowed: `[Soft Falsetto]`, `[Harmonies]`, `[Whispered]`. No artist names. Write numbers as words (三年, not 3年). Avoid English mid-line unless intended.
7. **Line length.** Verse lines 8–12 characters; chorus lines may run longer but must leave room to breathe.

## Self-check

- [ ] Every line end in a section matches its planned rhyme
- [ ] Hook appears 4+ times across the song
- [ ] Each verse has 2+ concrete images
- [ ] Final line is `[End]`

## Output

1. Lyrics in one code block (paste into Suno's Lyrics field)
2. One-line rhyme map, e.g. `Verse -ian · Pre -ou · Chorus -ai · Bridge -ang`
3. Then run Music-02 for the Style prompt
