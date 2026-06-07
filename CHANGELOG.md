# Changelog

What's new in each release of Phin. Newest first.

## 0.10.0 — 2026-06-07

- **OpenRouter support** — reach 300+ models (Claude, GPT, Gemini, DeepSeek, Llama…) with one key, alongside Anthropic / OpenAI / Gemini.
- **Mask PII before it reaches the AI** — redact email, phone, SSN, card, secrets, and DOB in results sent to your provider; your grid and exports keep the real values.
- **Smarter query plans** — color-coded EXPLAIN with a one-line verdict and one-tap explain & optimise.
- New app icon, **⌘/** shortcut search, and consistent empty states throughout.

## 0.9.0 — 2026-06-05

- Cleaner AI chat — stopping a reply ends cleanly, saved files confirm where they landed, smoother `@`-references.
- MongoDB sessions now show every connection's operations, with clearer connection errors.

## 0.8.0 — 2026-06-03

- **Schema diagrams (ERD)** — an interactive relationship map with primary/foreign-key badges, inferred links for databases without declared foreign keys, slow-path highlighting, and export to SVG / HTML / CSV / Mermaid / Graphviz. Works on Postgres, MySQL, SQLite, and MongoDB.

## 0.5.0 – 0.7.0 — late May 2026

- **AI that produces files** — export real query rows to CSV/JSON, build reports & dashboards (print to PDF), paste images into chat, get proactive next-step suggestions, and queue a follow-up mid-reply.
- **Import CSV / JSON / JSONL / Excel** into your database — as a new table or appended, with duplicate-conflict handling and a rejects inspector for rows that fail.
- **A real MongoDB workbench** — a mongosh-style terminal, inline document editing, a pill-style query builder, and a visual aggregation-pipeline builder.
- **macOS-native redesign** — vibrancy, sheet dialogs, popovers, a Spotlight-style command palette, and the warm cà phê sữa theme.
- Friendlier errors everywhere, safer destructive actions (dependency preview + optional backup), and large/JSON-heavy results that no longer freeze the app.

## 0.4.0 — 2026-05-20

- **Click-to-filter** — build filters from chips that read like a sentence, with AI-proposed filters, saved views, and a Source tab showing the compiled query.
- **Code interpreter** — a sandboxed Python tool for math SQL can't do (percentiles, correlation).

## 0.2.0 – 0.3.0 — mid May 2026

- **Three-tier AI permissions** (Reads / Writes / DDL) plus a production safety floor that refuses `DROP` / `TRUNCATE` outright.
- **Right-click everything**, multi-row selection, a column finder, and whole-table streaming export.
- A Spotlight-style command palette and test-before-save on the connection form.

## 0.1.0 — 2026-05-13

- First release: four databases — **PostgreSQL, MySQL, SQLite, MongoDB** — in one workbench, with a schema browser, query editor, virtualized result grid, AI chat with human-in-the-loop approval, and Keychain-secured credentials. Universal macOS app.
