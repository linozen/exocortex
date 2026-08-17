---
title: Inbox workflow
description: How material enters the vault (capture), how it traverses 21.01_Inbox, and how it leaves (triage to concepts/refs/antilibrary/archive). The 21-day rule that prevents another 922-line backburner.
tags:
  - concept
  - workflow
  - tools
author: claude-opus-4-7
authored_on: 2026-06-08
sources: []
certainty: A
certainty_notes: "Tier A for the file layout, Obsidian config, Sol script, and inbox template (all verified live on this machine on 2026-06-08). Tier B for the cadence parameters (21-day archive rule, Sunday triage cadence) — calibrated guesses, not measured."
---

The goal is to make capture cheap enough that nothing-worth-keeping gets lost, and triage cheap enough that nothing-worth-keeping rots in the inbox. The pipeline is short:

```
capture  →  21.01_Inbox/  →  triage  →  concepts / refs / antilibrary / archive
```

A previous "backburner" file accumulated to 922 lines before it was salvaged in three passes on 2026-06-06. The 21-day archive rule below exists to prevent that recurring.

## File convention

Inbox items live at `21.01_Inbox/<YYYY-MM-DD-HHmm>-<slug>.md`. The `<slug>` part is optional — the timestamp alone is enough to be unique. Frontmatter is minimal:

```yaml
---
captured_at: 2026-06-08T14:32
source:                  # URL, paper title, conversation, etc — optional
type: fragment           # one of: fragment | url | note | read | transcript
---
```

Tags, certainty, sources-with-keys, author — none of these are filled at capture. They are *triage outputs*, added when an item is promoted out of the inbox. The cost of inbox capture must stay near zero.

## Capture surfaces

### macOS — Sol launcher

A shell script at `~/.config/sol/scripts/inbox-capture.sh` (kept in sync at the vault root as `inbox-capture.sh` for editing convenience):

- Reads the macOS clipboard via `pbpaste`.
- If clipboard contains a URL → fills `source:`, sets `type: url`, leaves body empty.
- If clipboard contains other text → drops it into the body, sets `type: fragment`.
- If clipboard is empty → opens a blank note ready to dictate or type.
- Constructs an `obsidian://advanced-uri?...&mode=new` URL and `open`s it. Obsidian comes to the foreground with the new note focused on the body.

The script registers in Sol via the magic comments:

```bash
#!/usr/bin/env bash
# name: Inbox Capture
# icon: 📥
```

Trigger Sol → "Inbox Capture" (or whatever fuzzy match you've trained), and you're in a new inbox note in under a second.

### macOS — Obsidian directly

For longer captures while Obsidian is already open: command palette → "Templates: Insert template" → `inbox.md`. Or bind a hotkey to the same command. The template at `21.98_Templates/inbox.md` produces the same frontmatter as the script.

### Phone — not yet set up

Obsidian on the phone uses Obsidian Sync against the same vault, so anything written to `21.01_Inbox/` on the phone reaches the laptop. The specific capture surface (share-target, hotkey, custom launcher action) is **TBD** — none chosen or tested yet. Candidates and the URI mechanism that backs them are noted in [[capture-shortcuts]].

## Sync

Obsidian Sync handles macOS ↔ phone. Selective sync is **off** for `21.01_Inbox/` and `21.98_Templates/` (i.e. they sync); excluded folders are operator-defined and listed at Settings → Sync.

The vault is not under iCloud Drive (Documents-folder iCloud sync is disabled), so Obsidian Sync is the only sync layer touching these files.

## Triage cadence

**Sunday, ~15 min.** Open the vault in Obsidian on the laptop. Two-step prompt to Claude:

1. *"Archive any `21.01_Inbox/*.md` with `captured_at` older than 21 days into `21.99_Archive/inbox-2026-MM/`. Report count."* (Creates the monthly archive subfolder if missing.)
2. *"List remaining `21.01_Inbox/*.md` sorted by `captured_at`. For each, propose one of: promote to `21.02_Zettel/concepts/<slug>.md` (using `concept.md` template), promote to `21.02_Zettel/refs/<slug>.md` (using `ref.md` template), append a line to the appropriate `21.02_Zettel/refs/antilibrary/<queue>.md` (texts / courses / audiovisual), or discard. Show me the proposed destination per item before writing anything."*

User confirms per item; Claude writes destinations with appropriate frontmatter (`title`, `description`, `tags`, `author`, `authored_on`, `certainty`, `certainty_notes`) and `rm`s the inbox file.

**The rule that prevents a backburner**: every inbox item leaves the inbox by end of session. If it's not promotable and not discardable, it lands in the relevant `refs/antilibrary/<queue>.md` (one line, with a BBT citekey if available). The antilibrary queues are the only relief valve.

**Mid-week soft signal.** If inbox file count crosses ~20, run a triage pass mid-week. No calendar enforcement; the count is the trigger.

**Quarterly.** Skim `21.99_Archive/inbox-*` for anything that aged into relevance. Expect to skip most quarters.

## File layout this depends on

- `21.01_Inbox/` — capture target, normally near-empty
- `21.98_Templates/inbox.md` — 5-line frontmatter scaffold
- `21.98_Templates/concept.md`, `ref.md` — promotion destinations
- `21.99_Archive/inbox-YYYY-MM/` — created lazily by the 21-day archive step
- `21.02_Zettel/refs/antilibrary/{texts,courses,audiovisual}.md` — the three queues things land in when they don't yet warrant a ref note
- `~/.config/sol/scripts/inbox-capture.sh` — Sol launcher script
- `.obsidian/templates.json` — `{"folder": "21.98_Templates"}`

## Adjacent

- [[capture-shortcuts]] — the URI mechanism this workflow rides on
- [[obsidian-zotero-integration]] — parallel "workflow-on-tools" doc for the citation pipeline
- [[note-taking]] — the higher-level question this serves
- [[curation]] — what triage is, from the user's earlier framing
