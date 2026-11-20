# SPEC.md — Jhut AI build plan (final round)

Spec-driven plan. Each item has a goal, what "done" means, and its status.
Status: ✅ done · 🟡 demo · ⬜ planned.

## 1. Goal
Turn the browser prototype into a working sorting station that a yard can use for a
4-week pilot: photograph a bundle, get colour + fabric + grade + bin, and print a
Batch Passport that a buyer can trust.

## 2. Already built (preliminary round)
| # | Item | Status |
|---|---|---|
| 2.1 | Scan screen with camera/upload, EN + Bangla | ✅ |
| 2.2 | Real colour analysis and purity-based grade (A/B/C) | ✅ |
| 2.3 | 6 price bins, sorted vs unsorted value, uplift | ✅ |
| 2.4 | Batch list, Batch Passport, report | ✅ |
| 2.5 | Fabric type | 🟡 preset / texture heuristic |
| 2.6 | `/docs` pitch deck + technical docs with admin scheduling | ✅ |

## 3. Final-round work, in order
| # | Item | Done when | Status |
|---|---|---|---|
| 3.1 | **Fabric model.** Fine-tune EfficientNet on the Mobile-Captured Fabric Dataset (6 classes) plus our own yard photos | Held-out accuracy reported per class; confusion matrix saved | ⬜ |
| 3.2 | **On-device export.** ONNX → TFLite / TF.js, runs in the browser offline | Model under ~10 MB, under 1 s per photo on a mid-range phone | ⬜ |
| 3.3 | **Backend.** FastAPI + Pydantic, PostgreSQL + pgvector, photos in Cloudflare R2 | Bundles and passports saved and reloaded across devices | ⬜ |
| 3.4 | **Bangla summary.** Local LLM (Ollama, Gemma/Qwen ≤7B), Gemini as fallback; gets only computed numbers | Summary never contains a number that is not in the input (checked by code) | ⬜ |
| 3.5 | **Voice + OCR.** Whisper for Bangla voice notes, Tesseract for buyer slips | Voice note and slip attach to a batch | ⬜ |
| 3.6 | **Automation.** n8n / Prefect: daily report, price update, low-stock alert | Daily report sent without manual steps | ⬜ |
| 3.7 | **MCP server `jhut-ai-mcp`.** Tools: grade bundle, get batch, make passport, price lookup, daily report | Works from Claude Desktop over stdio and Streamable HTTP | ⬜ |
| 3.8 | **Dashboard.** Metabase / Chart.js: kg sorted, value uplift, grade mix | Yard owner sees today's numbers on one screen | ⬜ |
| 3.9 | **Deploy.** Docker on a cloud server; Cloudflare Tunnel for the yard-office PC | Public HTTPS link works from a phone | ⬜ |

## 4. Rules every item must follow
- Numbers come from code, never from the LLM (see `CLAUDE.md`).
- Bangla-first, offline-first, no personal data.
- Dataset licence must be checked before any trained model is shipped
  (the Kaggle fabric dataset licence is currently unknown).

## 5. Out of scope for the final round
- Payments, buyer marketplace, multi-yard accounts.
