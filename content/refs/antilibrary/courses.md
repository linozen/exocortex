---
title: Courses queue
description: MOOCs, university courses, lecture series, workshops, tutorials. Includes anything structured-as-curriculum.
tags:
  - antilibrary
  - queue
---

Promote each to a `refs/<key>.md` when you start taking notes on it.

## To process

### Salvaged from backburner (2026-06-08)

- _Advanced Python Mastery_ — David Beazley ([dabeaz-course/python-mastery](https://github.com/dabeaz-course/python-mastery))
- Larry McEnerney — _Leo Strauss Center: The Craft of Writing Effectively_ ([YouTube full lecture](https://www.youtube.com/watch?v=vtIzMaLkCaM))
- _Augmented Psychotherapy Training (APT)_ — MIND Foundation ([mind-foundation.org/apt](https://mind-foundation.org/apt/))
- _EMDR-Zertifizierung_ — EMDRIA ([emdria.de/zertifizierung](https://www.emdria.de/zertifizierung))
- _Compassionate Inquiry_ — Gabor Maté ([compassionateinquiry.com](https://compassionateinquiry.com/online-training/))

## Processed

```dataview
TABLE WITHOUT ID file.link AS "Note", authored_on AS "Worked on"
FROM "21.02_Zettel/refs"
WHERE medium = "course"
SORT authored_on DESC
```
