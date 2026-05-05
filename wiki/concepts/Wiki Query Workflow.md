---
title: Wiki Query Workflow
type: concept
tags: [llm-wiki, workflow, query]
sources:
  - "[[raw/clippings/2026-05-04-llm-wiki]]"
created: 2026-05-04
updated: 2026-05-04
---

# Wiki Query Workflow

The Wiki Query Workflow answers questions by searching the maintained wiki
first, then reading the most relevant pages and synthesizing an answer with
citations. It treats the wiki as the primary working interface rather than a
side effect of chat.

## Output Forms

A useful answer may become a new wiki page, a comparison table, a synthesis, a
canvas, a chart, or a slide deck. In the [[LLM Wiki Pattern]], valuable query
outputs should not disappear into chat history; they can be filed back into the
wiki so future work compounds.

## Relationship To Indexing

`wiki/index.md` is the starting map at moderate scale. When the wiki grows,
local search or graph-aware tools may become useful, but the index keeps the
workflow simple early on.

## Related

- [[LLM Wiki]]
- [[LLM Wiki Pattern]]
- [[Compounding Knowledge Base]]
- [[Wiki Ingest Workflow]]
