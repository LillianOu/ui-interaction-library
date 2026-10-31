---
name: 05-floating-label
description: Use when building form fields whose label floats above the value. Floating Label (浮動標籤) UI interaction recipe covering pointer, touch, keyboard, accessibility and reduced motion.
---
# 05 — 浮動標籤 / Floating Label

**Category:** 輸入與控制 / Inputs & Controls

## Effect

A form field shows its label inside the input as a placeholder-like prompt; when the field is focused or filled, the label moves up and shrinks to sit above the value. The field stays compact without ever losing its label, so the user always knows what the field is for.

## When to use

Use when building form fields whose label floats above the value. This skill is an interaction recipe, not an existing code component.

## Copy-ready English prompt

```text
Create a reusable floating label text field. The label sits inside the empty field and animates to a smaller position above the value when the field receives focus or contains a value, and returns only when the field is empty and blurred. Use a real <label> element associated with the input; never use the placeholder as the only label. Detect the filled state reliably, including browser autofill, programmatic values, pre-filled server values and values restored by the back button. Support text, email, number, password, date, select and textarea variants, with the label not overlapping native controls such as date pickers or select arrows. Keep sufficient contrast for the label in both positions, keep a visible focus style, and ensure the label remains readable at 200% zoom and with long or translated text. Show helper text and error messages below the field, linked with aria-describedby, and set aria-invalid on error. Handle disabled, read-only, required and optional states with text cues, not colour alone. With prefers-reduced-motion, move the label without animation. Avoid layout shift when the label moves, and work correctly in right-to-left layouts.
```
