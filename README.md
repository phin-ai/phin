<div align="center">
  <h1>Phin — AI-native data workbench for macOS</h1>
  <p><b>One desktop app for every database. AI that drips answers from your data.</b></p>
  <p><em>/fɪn/ · cà phê phin · ☕</em></p>
</div>

Phin is a native macOS app for working with **PostgreSQL, MySQL, SQLite, and MongoDB** through one warm workbench. Browse schemas, write queries, see results — and chat with an AI that knows your schema, drafts queries, and asks before running anything that writes.

```
┌────────────────────────────────────────────────────────────────────────┐
│  Datafabric dev / studio.users                            ⌘B  ⌘J  ⌘,  │
├────────────────┬───────────────────────────────────────┬────────────────┤
│  Datafabric    │  SELECT * FROM users                  │  Phin          │
│  postgres ▾    │  WHERE last_seen >= now() - '7d';     │                │
│                │  ──────────────────────────────       │  How many      │
│  SCHEMA  · 268 │   id   │  email     │  plan  │  …    │  pro users     │
│  ▼ studio      │   8a4  │  m@…       │  pro   │       │  signed up     │
│    • users     │   8b2  │  k@…       │  free  │       │  this month?   │
│    • orders    │                                       │                │
│  ▶ public      │                                       │  Approve ▶ ✓   │
│  ● 12ms · pg16 │  Data · Structure · Plan              │                │
└────────────────┴───────────────────────────────────────┴────────────────┘
```

## Why Phin

- **One app, every database.** Postgres, MySQL, SQLite, MongoDB — same UI, same chat, same approval flow.
- **Chat that knows your schema.** Pin tables with `@-mentions` — drill into columns with `@table.`. Phin writes against the columns you actually have, not the columns it guessed. Bring your own key — Anthropic, OpenAI, Gemini, or OpenRouter (300+ models).
- **Use it from Claude Code.** Phin ships a local connector so you can explore your saved connections from Claude Code — list connections, browse schemas, preview tables, and run read-only SQL or MongoDB queries. Read-only by default; passwords never leave your Keychain. One-click setup in **Settings → Claude Code**.
- **Safety floor for writes.** Reads can auto-approve; writes and schema changes always need explicit approval. Production-tagged connections refuse `DROP TABLE` / `TRUNCATE` regardless.
- **Passwords stay on your Mac.** Saved to the macOS Keychain. Never written to disk in plaintext, never sent to the AI.
- **Native macOS feel.** Vibrancy throughout, Spotlight-style command palette, sheets, warm cà phê sữa theme.

## Download

**[⬇︎ Download the latest release](https://github.com/phin-ai/phin/releases/latest)** — a universal macOS app (Apple Silicon + Intel), ~35 MB, self-contained.

1. Download **`Phin-<version>-macOS.zip`** and unzip it.
2. Drag **Phin** into your **Applications** folder.
3. **First open.** Phin isn't notarized yet, so macOS blocks it once with *"Apple could not verify 'Phin' is free of malware…"*. To approve it, either:
   - **Settings:** double-click Phin → click **Done** → open **System Settings → Privacy & Security**, scroll to **Security**, and click **Open Anyway** next to the Phin notice. Confirm — Phin launches and opens normally from then on. **or**
   - **Terminal (faster):** clear the download-quarantine flag once, then open Phin normally:
     ```bash
     xattr -dr com.apple.quarantine /Applications/Phin.app
     ```

> **Beta note.** Phin is in **free public beta**. AI chat in this build is enabled **through 30 September 2026**; the rest of the app keeps working after that. New builds will extend it.

## First run

1. **Connect.** Welcome screen → **New connection**. Pick your database, enter host / user / password. The password goes straight to your Keychain.
2. **Browse.** Sidebar shows your schemas / collections. Click a table to preview rows.
3. **Query.** Write SQL in the editor (`⌘⏎` runs the statement at the cursor). Results land in a virtualized grid.
4. **Chat.** Open the AI panel (`⌘J`). Add your LLM API key in **Settings → Ask Phin** (Anthropic, OpenAI, Gemini, or OpenRouter). Ask a question — Phin drafts a query and asks before running it.

## Supported databases

| Engine | Status |
|---|---|
| PostgreSQL | ✅ Full support |
| MySQL | ✅ Full support |
| SQLite | ✅ Full support |
| MongoDB | ✅ Full support |

## Keyboard shortcuts

| | |
|---|---|
| `⌘⏎` | Run statement at cursor |
| `⌘P` | Command palette (tables / chats / recent queries / connections) |
| `⌘J` | Toggle chat panel |
| `⌘B` | Toggle sidebar |
| `⌘N` | New connection |
| `⌘,` | Settings |
| `⌘L` | Add selection to chat |
| `⌘C` | Copy selected rows as TSV |
| `⌘/` | Search all shortcuts |

Full shortcut list lives in **Settings → Shortcuts**.

## Feedback

Phin is in active development and feedback shapes what ships next. Found a bug, want a feature, or hit something confusing?

**[→ Open an issue](https://github.com/phin-ai/phin/issues/new)**

Every report is read. Thank you for trying Phin. 🙏

## Changelog

See [CHANGELOG.md](CHANGELOG.md) for what's new in each release.

## License

Phin is currently in **free public beta**. © 2026 Phin AI. All rights reserved. The application is free to use during the beta period; the source is not currently public.

<div align="center"><sub>Slow-brewed for your data. One steady drip at a time. ☕</sub></div>
