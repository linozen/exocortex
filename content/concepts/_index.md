---
title: Concepts
author: Linus Sehn
authored_on: 2025-02-10
---

Index of concept notes — material with more of my own thinking and organizing than the source-summarizing [[refs/_index|refs]]. Grouped by theme via tags; lists are Dataview-rendered, so the index itself contributes no edges to the graph view.

## Meaning, sense-making, meta-crisis

The civilizational-scale strand. Different traditions converging on similar diagnoses.

```dataview
LIST description
FROM #meta-crisis AND #concept
SORT file.name ASC
```

## Cognition, epistemology, method

```dataview
LIST description
FROM #epistemology AND #concept
SORT file.name ASC
```

## Psychotherapy, parts, self

```dataview
LIST description
FROM #psychotherapy AND #concept
SORT file.name ASC
```

## Pharmacology, neuroscience, hormones

```dataview
LIST description
FROM #pharmacology AND #concept
SORT file.name ASC
```

## Surveillance, technology, power

```dataview
LIST description
FROM #surveillance AND #concept
SORT file.name ASC
```

## Social science, institutions

```dataview
LIST description
FROM #institutions AND #concept
SORT file.name ASC
```

## Economics, finance

```dataview
LIST description
FROM #economics AND #concept
SORT file.name ASC
```

## Epidemiology

```dataview
LIST description
FROM #epidemiology AND #concept
SORT file.name ASC
```

## Programming, computing

```dataview
LIST description
FROM #programming AND #concept
SORT file.name ASC
```

## Workflows

```dataview
LIST description
FROM #workflow AND #concept
SORT file.name ASC
```

## Uncategorised

A backstop: concepts not yet assigned to a thematic group. If this list grows, add a tag or a new section above.

```dataview
LIST
FROM #concept
WHERE length(intersect(file.tags, ["#meta-crisis", "#epistemology", "#psychotherapy", "#pharmacology", "#surveillance", "#institutions", "#economics", "#epidemiology", "#programming", "#workflow"])) = 0
SORT file.name ASC
```
