# AGENTS.md — Jhut AI

Instructions for any AI coding agent (Claude Code, Copilot, Cursor, Codex, etc.).
The full rules are in `CLAUDE.md`; the build plan is in `SPEC.md`. This is the short version.

## Before you start
- Read `CLAUDE.md` (rules, current state) and `SPEC.md` (what to build next).
- Check which parts are **live**, **demo** or **planned**. Do not mix them up in code or text.

## Rules
- **Numbers from code only.** Prices (Tk/kg), weights, grades and totals are calculated by
  deterministic functions. LLM output may describe them but never create or change them.
- **Bilingual.** Every new UI string gets English and Bangla text.
- **Offline first.** Sorting a bundle must work with no internet.
- **No secrets, no personal data** in commits (API keys, worker names, phone numbers, faces).
- **Prototype stays one file.** `index.html` must run by double-click, no build tools.

## Grading logic (do not change without updating SPEC.md)
- Grade A: colour purity >= 0.85
- Grade B: colour purity >= 0.62
- Grade C: everything else
- Bin prices and the unsorted price live in the `BINS` and `UNSORTED` constants in `index.html`.

## Done means
1. It works in the browser at phone width.
2. English and Bangla both show correctly.
3. No console errors.
4. `docs/content.json` updated if a feature changed status (live / demo / planned).
5. One clear commit message.
