# Changelog

What's new in each release of Phin. Newest first.

## 0.14.9 — 2026-07-21

- **Postgres functions that exist in more than one form now open instead of erroring** — clicking a function with several versions (like pgvector's `cosine_distance`, which has a separate version for each vector type) used to fail with a "more than one function" error. Each version now shows as its own entry, labeled with its arguments, and opens to exactly that version's definition.
- **The Functions, Views, Procedures and other object lists now have a search box** — the filter the Tables list already had is now on every object tab, so you can quickly narrow a long list of functions, views, sequences, enums or extensions by name.

## 0.14.8 — 2026-07-20

- **Bulk MongoDB updates that write results back to a collection now work** — aggregations ending in a `$merge` or `$out` stage (the standard way to compute a value per group and write it to every matching document in one pass, like setting a category array on each tenant from its products) were silently rejected. Phin was adding an internal row cap after the write stage, which MongoDB doesn't allow there. The cap is now skipped for these pipelines, so they run in a single step instead of one update per document.

## 0.14.7 — 2026-07-20

- **MongoDB filters on true/false and number fields now match your data** — in the MongoDB query builder, filtering a boolean field (*is true* / *is false*) or a number field with "is", "is not", or "is one of" compared the value as text, so it silently matched no documents. Filters now send the value with the right type, and each condition shows a small colored dot for the type Phin detected (blue = text, green = number, amber = true/false). Digit-heavy text like zip codes or phone numbers is kept as text so it still matches.

## 0.14.6 — 2026-07-19

- **Chat titles and suggested follow-ups are more consistent** — the quick helper calls that name a new chat and offer next-step prompts now run with fixed, deterministic settings, so the same conversation reliably gets the same title and the same quality of suggestions, instead of occasionally drifting into odd phrasings.

## 0.14.5 — 2026-07-02

- **Multi-line text keeps its line breaks** — editing or copying a value that spans several lines, like a Markdown field in a MongoDB document or a long text cell in a SQL table, no longer squashed everything onto one line. These values now open in a multi-line editor and keep their formatting when you copy them out or save an edit.

## 0.14.4 — 2026-07-01

- **A fixed export no longer looks like it failed** — when Phin's first attempt to save query results hit an error and it retried successfully, the old "Failed" card stayed on screen next to the file it had just produced, making it look like Phin couldn't recover when it actually had. The failed card now clears as soon as the file is written.
- **Mentioning a table with @ works cleanly** — picking a table from the `@` suggestion list now closes the list and inserts the name once. It previously left the list open and, on a second Enter, kept tacking the table's name onto itself (`…_2024_h1_2024_h1…`). Typing `.` right after an inserted table still opens its column list.

## 0.14.3 — 2026-06-29

- **Backing up or exporting several tables now saves the right data** — asking Phin to export multiple query results at once could previously save the *last* query's rows into every file, so a "back up these 3 tables" request quietly produced files with the wrong contents. Each export now runs its own query and writes its complete, correct result, and exports are read-only (a query that would write or change data is refused).

## 0.14.2 — 2026-06-29

- **Answers from a single query instead of re-running it** — once Phin runs a query, it now knows the results are already on your screen and replies straight away, instead of running the same query again to "show" them. If it does repeat (even a reworded or reformatted version of the same query), it's caught and stopped right away.

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
