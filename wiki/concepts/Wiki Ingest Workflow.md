---
title: Wiki Ingest Workflow
type: concept
tags: [llm-wiki, workflow, ingestion]
sources:
  - "[[raw/clippings/2026-05-04-llm-wiki]]"
created: 2026-05-04
updated: 2026-05-04
---

# Wiki Ingest Workflow

The Wiki Ingest Workflow is the process for converting a new source into
durable wiki structure. In the [[LLM Wiki Pattern]], ingest is where the wiki
compounds: a source becomes summaries, concept updates, entity links, and index
entries.

## Steps

1. Capture the source in `raw/` with metadata and provenance.
2. Extract key concepts, entities, contradictions, and useful claims.
3. Create or update source, concept, entity, and synthesis pages in `wiki/`.
4. Add bidirectional `[[wikilinks]]` where they clarify relationships.
5. Update `wiki/index.md` so later queries can find the relevant pages.

## Design Pressure

Ingest should preserve the distinction between immutable source records and the
LLM-maintained wiki. The raw source remains the reference point; the wiki is the
working synthesis.

## Related

- [[LLM Wiki]]
- [[LLM Wiki Pattern]]
- [[Wiki Query Workflow]]
