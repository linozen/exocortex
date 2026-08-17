---
title: Obsidian + Zotero integration
description: How the exocortex citation workflow actually wires up — Better BibTeX → Pandoc Reference List + zotero-mcp → ref notes
tags:
  - concept
  - workflow
  - tools
author: claude-opus-4-7
authored_on: 2026-06-08
sources: []
certainty: A
certainty_notes: "Tier A for the plugin set and paths (verified live against `.obsidian/community-plugins.json` and `obsidian-pandoc-reference-list/data.json` on 2026-06-08). Tier B for workflow specifics that depend on plugin/MCP versions — re-verify if you upgrade Obsidian, Pandoc Reference List, or zotero-mcp."
---

This is the actual setup as of 2026-06-08, not the aspirational one. If you change plugins or paths, update this note.

The stack was trimmed from four moving parts to three on 2026-06-08. The Zotero Integration plugin (`obsidian-zotero-desktop-connector` by mgmeyers) was removed: its citation-insert command was redundant with Pandoc Reference List's `@`-autocomplete, and its note-import path had been configured into a no-op.

## The pieces

| Piece                                          | Role                                                                                                                                                       |
| ---------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Zotero** (desktop app)                       | Source of truth for bibliographic records and PDFs. Read and annotate here.                                                                                |
| **Better BibTeX** (Zotero plugin)              | Continuously exports the library to `references.bib` at the vault root. Owns citation-key generation.                                                      |
| **Pandoc Reference List** (Obsidian plugin)    | The only Obsidian-side citation plugin. Provides `@`-typed fuzzy autocomplete from `references.bib`, hover tooltips on `@key`, and a sidebar bibliography. |
| **Pandoc binary** (`/opt/homebrew/bin/pandoc`) | Invoked on every render by Pandoc Reference List — once per tooltip, once per sidebar bibliography. Hot path, not a fallback.                              |
| **zotero-mcp**                                 | Drives everything write-side from this harness: add-by-DOI/ISBN/URL, ref-note generation, annotation extraction (`mcp__zotero__zotero_*`).                 |

## What's wired up right now

- **BBT export target**: `/Users/lino/Documents/20-29_Plan_Research_Learn/21_Exocortex/references.bib`, auto-updated.
- **Pandoc Reference List bibliography path**: same as above (verified in plugin `data.json`).
- **Pandoc binary path**: `/opt/homebrew/bin/pandoc` (Homebrew install).
- **CSL style**: APA from the official `citation-style-language/styles` GitHub mirror; language `en-GB`.
- **Pandoc Reference List flags**: `renderCitations: true`, `renderCitationsReadingMode: true`, `enableCiteKeyCompletion: true`, `showCitekeyTooltips: true`, `renderLinkCitations: true`, `pullFromZotero: true`. (`renderLinkCitations` could be flipped to `false` — the vault overwhelmingly uses bare `@key`, not `[[key]]` — but it costs nothing left on.)
- **Citation key format** in ref-note filenames: `21.02_Zettel/refs/<citation_key>.md`, matching the BBT key (e.g. `juliano2004.md`).

## Workflow

1. **Add a source.** Drag a PDF into Zotero, or ask Claude to call `mcp__zotero__zotero_add_by_doi` / `_by_isbn` / `_by_url`. Verify the BBT citation key (right-click → Better BibTeX → Citation Key). See the gotchas below.
2. **Read and annotate.** Open the PDF inside Zotero's reader. Highlights and sticky notes auto-save.
3. **Cite while writing.** In any note, type `@` — Pandoc Reference List offers fuzzy completion against `references.bib` (matches on citekey, title, author) and inserts bare `@key`. For the bracketed form, wrap by hand: `[@key, p. 12]`, `[@key, pp. 12-15]`, multi-cite `[@key1; @key2]`.
4. **Generate a ref note.** Ask Claude — phrasings like "ref note for `@juliano2004`", "ref-note this DOI", or "make a ref note for the paper I just annotated". The harness resolves the item (`zotero_search_by_citation_key` / `zotero_search_items` / `zotero_get_recent`), pulls metadata (`zotero_get_item_metadata`, format `markdown`, with abstract), pulls highlights (`zotero_get_annotations`), formats the `## Highlights` block in source order with proper page locators, and writes `21.02_Zettel/refs/<bbt-citekey>.md`. If the file exists, existing highlights are merged into rather than overwritten.
5. **See the bibliography.** Pandoc Reference List's **sidebar view** enumerates the works cited in the active note (`@key` mentions). There is no in-body `## Bibliography` section — the sidebar is canonical.
6. **After any MCP add**, run `mcp__zotero__zotero_update_search_database` so the MCP's semantic search picks up the new item.

## Ref-note frontmatter convention

```yaml
---
title: "Notes on: <title> (<Author> <year>)"
description: <one line>
tags:
  - <kebab tags>
author: Linus Sehn | claude-opus-4-7
authored_on: YYYY-MM-DD
citation_key: <bbt key>
certainty: A | B | C | D | E
certainty_notes: <why that tier>
---

## Highlights

[@<key>, p.<page>]:
> quote
```

No `## Bibliography`, no `[^ref]` placeholder. Pandoc Reference List's sidebar covers that surface.

## Provenance schema fields

`author`, `authored_on`, `sources`, `certainty`, `certainty_notes` are first-class metadata across the vault. Notes written by a model carry `author: claude-opus-4-7` (or the model used); notes by you carry `author: Linus Sehn`. The `certainty` tier follows the [global tiering rules](file:///Users/lino/.claude/CLAUDE.md): A = directly cited from authoritative source verified in-context, down to E = speculation.

## Publishing target

**Currently undecided.** This vault previously published to Hugo (artefacts of that workflow — TOML frontmatter, `relref` shortcodes, `ox-hugo` paths — were cleaned out on 2026-06-06). When/if a publish target is chosen, the provenance fields above are designed to map cleanly:

- `author` → byline; show a model icon when `!= "Linus Sehn"`
- `authored_on` → page date or "written on" stamp
- `sources` → "Sources" list at the foot, each item linking to `refs/<key>/`
- `certainty` + `certainty_notes` → a coloured callout (A = green/none; B = yellow; C = orange; D/E = red) and a filter facet

## Gotchas observed

1. **Trashed items reserve their BBT keys.** Adding Juliano2004 by DOI and then re-adding it via PDF (to attach the file) sent the first import to trash but it kept `juliano2004`, forcing the replacement to `juliano2004a`. Fix: empty Zotero's Trash, then refresh the citation key in BBT — the suffix drops.
2. **Multi-word surnames break the default BBT formula.** Rocha Cabrero & Hamilton initially got a placeholder key (`zotero-item-NNN`). Pinning via the Extra field over the MCP didn't propagate immediately. Fix in Zotero UI: right-click → Better BibTeX → **Pin Citation Key**. The pin survives metadata changes.
3. **Citation keys are the only stable linking primitive.** Do not store the 8-character internal Zotero item key (e.g. `Z4FD9DSS`) in frontmatter — those are regenerated on sync. Use the BBT citation key as the stable identifier (`citation_key: juliano2004`).
4. **`@key` resolution requires Pandoc.** Obsidian itself doesn't expand `@key` natively. Pandoc Reference List supplies the renderer, calling the external `pandoc` binary on demand.
5. **PDF retrieval.** Springer/Elsevier paywalls often defeat the BBT/MCP auto-fetch. sci-hub.mk works with a realistic User-Agent header (curl with a Chrome UA succeeded for Juliano2004; the embedded PDF lives at `sci.bban.top/pdf/<DOI>.pdf`). The MCP `zotero_add_from_file` then re-derives metadata from the PDF's embedded DOI.

## Plugin config file

- `.obsidian/plugins/obsidian-pandoc-reference-list/data.json` — Pandoc binary path, bibliography path, CSL style, tooltip / autocomplete / link-citation toggles.

## See also

- [[caffeine-withdrawal]] — the test case that surfaced gotchas 1–2, 5
- [[note-taking]]
- [[antilibrary/_index|antilibrary]] — the three queues (texts, courses, audiovisual) feeding this pipeline
