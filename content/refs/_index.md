---
title: References
author: Linus Sehn
authored_on: 2024-03-06
---

Index page for reference notes. These notes generally don't express my own thinking but aim to summarise and make available what I found interesting about the thinking of others. Source material can be (audio)books, articles, blog posts, university lectures, movies, or anything else I found interesting.

If you wonder where I find the stuff that ends up here, take a look at [[input-channels]]. The active queues — by medium — live under [[antilibrary/_index|antilibrary]].

## Highlights

A few favourites worth singling out:

- Earley, J. (2012). _Self-Therapy: A Step-By-Step Guide to Creating Wholeness and Healing Your Inner Child Using IFS_ — [[earley2012]]
- Foucault, M. (1975). _Surveiller et punir_ — [[foucault1975]]
- Bucay, J. (2017). _Ich will_ — [[bucay2017]]
- Pagade, G. (2026). _Cognitive Debt: When Velocity Exceeds Comprehension_ — [[pagade2026]]
- The Consilience Project — _Glossary_ — [[consilience-glossary]]

## Full list (auto)

```dataview
TABLE WITHOUT ID file.link AS "Ref", medium AS "Medium", description AS "Description"
FROM #ref
SORT medium ASC, file.name ASC
```

## People

```dataview
TABLE WITHOUT ID file.link AS "Person", description AS "Domain"
FROM #person
SORT file.name ASC
```

## Queues

```dataview
TABLE WITHOUT ID file.link AS "Queue", description AS "What lives here"
FROM #queue
SORT file.name ASC
```

## The process

Roughly, my note-taking process is:

1. I find interesting material and capture it (see [[inbox-workflow]]).
2. I process it — see [[docs#Processing layer]] — and write a `refs/<bibkey>.md` summary with highlights and a bibliography reference, tagging it `ref` and setting `medium:` so it shows up in the right index automatically.
