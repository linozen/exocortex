---
title: Capture shortcuts
description: One-shot URI invocations that create a timestamped, frontmatter-filled inbox note on either macOS or the phone — backed by the obsidian-advanced-uri community plugin.
tags:
  - concept
  - workflow
  - tools
author: claude-opus-4-7
authored_on: 2026-06-08
sources: []
certainty: B
certainty_notes: "Tier B — built on the `obsidian-advanced-uri` URL schema as documented at vinzent03.github.io/obsidian-advanced-uri. The exact filepath template (`{{date:...}}`) is plugin-version-sensitive; verify after plugin upgrades."
---

The `obsidian-advanced-uri` plugin lets you open Obsidian to a *new note* with a *pre-filled body*, all via URL. Combined with a system-level launcher, it collapses "open Obsidian, navigate to Inbox, new note, type frontmatter" to one keystroke or tap.

The pattern below creates `21.01_Inbox/<timestamp>-note.md` containing the same frontmatter as `21.98_Templates/inbox.md`.

## The URL

```
obsidian://advanced-uri?vault=21_Exocortex&filepath=21.01_Inbox/{{date:YYYY-MM-DD-HHmm}}-note.md&data=---%0Acaptured_at%3A%20{{date:YYYY-MM-DDTHH:mm}}%0Asource%3A%0Atype%3A%20fragment%0A---%0A&mode=new
```

`vault` is whatever Obsidian calls the vault (check the lower-left vault switcher). `data` is URL-encoded — `%0A` is newline, `%20` is space. The frontmatter shape matches `21.98_Templates/inbox.md`; keep both in sync if either changes.

## macOS — Sol launcher script

Primary path. A shell script at `~/.config/sol/scripts/inbox-capture.sh` reads the macOS clipboard (`pbpaste`) and constructs the URL above with clipboard-aware frontmatter (URL → `source:`, text → body). Sol's `# name:` / `# icon:` magic comments make it show up as an action in the launcher. See [[inbox-workflow]] for the full script content.

## macOS — Raycast or Alfred (alternative)

If you prefer Raycast or Alfred over Sol, the same URL works as a Quicklink. No clipboard awareness (the script wraps that) — you get the bare empty-frontmatter note.

## Phone

Phone-side capture is **not yet decided**. Obsidian Android + Obsidian Sync are in place, so anything created in `21.01_Inbox/` on the phone syncs to the laptop. Candidate surfaces (none tested yet):

- Obsidian Android share-target: Settings → Files & links → "Default location for new notes" = `21.01_Inbox/`. Share-to-Obsidian then lands in the inbox.
- The same `obsidian://advanced-uri?...` URL bound to whatever launcher / shortcut surface the phone uses.
- Direct in-app capture using `21.98_Templates/inbox.md` via the Templates plugin.

Revisit once a primary surface is chosen.

> [!todo] Open: evaluate QuickAdd plugin
>
> The `QuickAdd` community plugin would let a single command-palette entry create a file with the timestamped `YYYY-MM-DD-HHmm-note.md` name + inbox frontmatter on both desktop and mobile — replacing the Shortcut/URI dance and removing the desktop/phone surface split. Cost: one more community plugin to maintain. Defer until iOS Shortcut + Advanced URI is actually painful in practice.

## Variants

- A hotkey from inside Obsidian rather than the OS: bind `Advanced URI: copy URI for active file` to a hotkey and reuse, or use the plugin's "Open URI" command with a saved URI.
- Voice-only capture: open the inbox URI → dictate via the system STT → the resulting note is no different from a typed one.

## Adjacent

- [[obsidian-zotero-integration]] — the other vault workflow that depends on a community plugin
- [[note-taking]] — the higher-level question this serves
