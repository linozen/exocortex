---
title: People queue
description: People you've noticed but haven't yet stubbed at refs/people/<name>.md. The discovery edge of the people tracking system.
tags:
  - antilibrary
  - queue
  - people
---

A person isn't a one-shot engagement — they're tracked over time. Once you've noted enough about someone to write 4–5 lines (domain, where to find them, why noticed), promote them to a stub at `refs/people/<slug>.md` and remove the bullet here.

The current people stubs (and a Dataview-driven all-people index) live at [[people/_index|refs/people/_index]].

## To stub

_(empty — populate as new people surface from inbox triage)_

## Promoted (Dataview)

```dataview
TABLE WITHOUT ID file.link AS "Person", description AS "Domain"
FROM "21.02_Zettel/refs/people"
WHERE file.name != "_index"
SORT file.name ASC
```

## Adjacent

- [[antilibrary/_index|antilibrary _index]] — the other queues
- [[people/_index|refs/people/_index]] — the per-person stub folder this feeds
