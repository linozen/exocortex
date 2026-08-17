---
title: Antilibrary
description: Three medium-queues of what to engage with next, plus a people queue and a Dataview-driven view of what's already been processed into ref notes.
tags:
  - antilibrary
---

The [[antilibrary]] proper: things I have signalled an intent to engage with but have not yet processed into a ref note. Split by medium because the commitment profiles vary.

## The queues

```dataview
TABLE WITHOUT ID file.link AS "Queue", description AS "What lives here"
FROM #queue
SORT file.name ASC
```

## Convention

The first three queues are by medium, and have two sections each:

- **`## To process`** — manually-maintained list of items waiting. Format is free; entries with `@bibkey` are in Zotero, the rest are bare URLs or annotations.
- **`## Processed`** — Dataview block over ref notes in `21.02_Zettel/refs/` whose frontmatter contains the matching `medium:` field. Auto-updated; no manual upkeep.

When you process an item, write the ref note (which gets `medium: <queue-name>`) and remove the bullet from `## To process`. The item then disappears from the to-process list and reappears in the processed view automatically.

The **people queue** has different semantics: a person isn't a one-shot engagement. Entries stay until the person is promoted to a `concepts/<name>.md` synthesis page — typically once 2–3 of their works have ref notes or their thinking starts threading through your own writing.

## Adjacent

- [[antilibrary]] — the underlying concept
- [[inbox-workflow]] — how items reach a queue in the first place
