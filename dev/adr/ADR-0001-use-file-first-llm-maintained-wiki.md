---
title: Use a file-first LLM-maintained wiki
type: adr
status: proposed
decision-date: 2026-05-05
deciders: [me, Codex]
tags: [llm-wiki, obsidian, file-over-app, knowledge-management]
supersedes: []
superseded-by: []
---

# ADR-0001: Use a file-first LLM-maintained wiki

## Context

This vault is being shaped around the [[LLM Wiki Pattern]]: raw sources remain
immutable, while an LLM maintains a structured `wiki/` layer of concepts,
entities, source summaries, and indices. The first ingests created pages for
[[LLM Wiki]], [[File over app]], [[Compounding Knowledge Base]], and related
workflows.

The vault also needs to remain portable across machines and resilient over time.
[[File Over App]] argues that durable work should live in user-controlled files,
not only in app state, cloud services, databases, or proprietary formats. This
matches the current repository direction: `.codex/`, `raw/`, `wiki/`, and
`dev/` are ordinary files that can be versioned and moved.

Known constraints:
- `raw/` is read-only source material.
- `wiki/` is LLM-maintained and should be navigable through [[Wiki Index]].
- `dev/` is collaborative and requires care around ADRs and debriefs.
- The system should work without requiring a separate RAG database at the start.

## Decision

We will use this Obsidian vault as a file-first, LLM-maintained wiki: sources
will be captured as files in `raw/`, durable synthesis will be maintained in
`wiki/`, and project decisions will be recorded in `dev/adr/`.

## Consequences

### Positive

- The vault stays portable because the primary artifacts are markdown files.
- Ingested knowledge can compound through links, summaries, and updated concept
  pages instead of being rediscovered from raw sources each time.
- Git history can track changes to the knowledge base and agent configuration.
- The workflow aligns with both [[LLM Wiki Pattern]] and [[File Over App]].

### Negative / trade-offs

- The wiki requires ongoing maintenance discipline: frontmatter, links, index
  updates, and contradiction handling can drift if agents do not follow the
  schema.
- Early search will depend mostly on files, links, and `wiki/index.md`, which
  may become insufficient as the vault grows.
- LLM-generated synthesis can introduce errors unless source citations and raw
  records remain easy to inspect.

### Neutral

- This does not forbid future search tools, graph tools, or MCP integrations.
- This does not require every chat answer to become a wiki page.
- This keeps Obsidian useful as an interface, but does not depend on Obsidian as
  the only way to read the vault.

## Alternatives considered

- Use app-native storage only. Rejected because it weakens portability and
  conflicts with [[Durable Digital Artifacts]].
- Use a RAG database as the primary knowledge layer. Rejected for now because
  the vault is small enough for markdown files, wikilinks, and [[Wiki Index]] to
  provide the first navigation layer.
- Keep all synthesis in chat history. Rejected because useful analysis would not
  compound inside the vault.

## References

- [[raw/clippings/2026-05-04-llm-wiki]]
- [[raw/clippings/2026-05-05-file-over-app]]
- [[LLM Wiki Pattern]]
- [[File Over App]]
- [[Compounding Knowledge Base]]
- [[Wiki Ingest Workflow]]
