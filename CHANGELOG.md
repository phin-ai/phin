# Changelog

What's new in each release of Phin. Newest first.

## 0.14.0 — 2026-06-29

- **No more getting stuck on the same query** — when Phin answered a question by running a query, it could occasionally re-run the exact same query over and over instead of replying, wasting time and looking broken. That loop is now caught and stopped, so Phin answers from the first result.

## 0.13.0 — 2026-06-21

- **Ask Claude Code about your data** — Phin ships a local connector for Claude Code, so you can explore your databases right from your editor: list saved connections, browse schemas, describe and preview tables, and run read-only SQL or MongoDB queries through the connections you've already set up. **Read-only by default** (writes are refused), passwords stay in the macOS Keychain and are never sent to the model, and large results are trimmed so a wide query won't flood the conversation.
- **One-click setup** — a new **Settings → Claude Code** screen wires everything up with a single button (or shows the exact command to copy if Claude Code's CLI isn't found). Phin is also installable from the Claude Code plugin marketplace.
- **Stop a slow tunnel test** — the **Stop** button now cancels a hanging SSH tunnel test immediately, instead of making you wait for the timeout.
- **Safer SQL editor** — statements that quietly write (`SELECT … INTO`, and `EXPLAIN ANALYZE` on a write) now ask for the same confirmation as any other write.

## 0.12.0 — 2026-06-17

- **MongoDB array editing** — change or delete a single element inside an array field without disturbing the rest of the document; the items you didn't touch keep their exact type.

## 0.11.0 — 2026-06-17

- **Reference a column, not just a table** — after you `@`-mention a table in chat, type a dot (`@orders.`) to list and insert its exact column names.
- **Copy rows with ⌘C** — select rows in the results grid and copy them as tab-separated values, ready to paste into a spreadsheet.
- **Quieter WHERE filter suggestions** — the quick filter's column list shows only where a column actually fits and stays out of the way while you type a value.

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
