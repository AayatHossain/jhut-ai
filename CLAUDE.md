# CLAUDE.md — Jhut AI

Project rules for Claude Code (and any AI coding assistant) working in this repo.
Read this file and `SPEC.md` before changing anything.

## What this project is
Jhut AI is a sorting station for garment waste (*jhut*) in Bangladesh. A phone camera
photographs a bundle, the app reads its colour and fabric, gives a grade (A/B/C),
puts it in a price bin, and builds a Batch Passport for the buyer.

## Current state (be honest about it)
| Part | Status |
|---|---|
| `index.html` prototype (scan, batch, passport, report; EN + Bangla) | **Live** on GitHub Pages |
| Colour analysis (`analyseColour`, `nameColour`) | **Real**, runs in the browser |
| Fabric type | **Demo**: preset for sample images, texture heuristic for uploads. Not a trained model yet |
| `docs/` pitch deck + technical docs | **Live**, content from `docs/content.json` |
| Backend, database, LLM summaries, MCP server | **Planned** for the final round (see `SPEC.md`) |

Never describe a demo or planned part as working.

## Hard rules
1. **Numbers come from code, never from the AI.** Prices, weights, grades and totals are
   computed by deterministic code. An LLM may only write text *about* numbers it is given.
2. **Bangla first.** Every user-facing string needs an English and a Bangla version.
   Sorters use the Bangla screen.
3. **Works offline on a cheap phone.** No feature may need a network call to sort a bundle.
4. **No personal data in the repo.** No worker names, phone numbers or photos of people.
5. **Keep the prototype a single file.** `index.html` must open from disk with no build step.

## Folder layout
```
index.html          prototype app (single file, no build)
docs/index.html     /docs module (pitch deck + technical docs + admin)
docs/content.json   all docs text, edited by hand or via docs/?admin
docs/config.json    docs visibility window (Bangladesh time, UTC+6)
CLAUDE.md AGENTS.md SPEC.md   rules and plan for AI assistants
```
Planned for the final round: `model/` (training + export), `api/` (FastAPI),
`mcp/` (jhut-ai-mcp server), `infra/` (Docker, Cloudflare Tunnel).

## Workflow
- Small commits, one change each, clear message.
- Test the prototype by opening `index.html` in a browser (mobile width too) before committing.
- After a push, GitHub Pages takes about 1 minute to update.
- To change docs visibility, edit `docs/config.json` and push.
