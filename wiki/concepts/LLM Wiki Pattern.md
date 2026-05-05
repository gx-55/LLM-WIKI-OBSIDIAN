---
title: LLM Wiki Pattern
type: concept
tags: [llm-wiki, knowledge-management, agent-workflow]
sources:
  - "[[raw/clippings/2026-05-04-llm-wiki]]"
created: 2026-05-04
updated: 2026-05-04
---

# LLM Wiki Pattern

The LLM Wiki Pattern uses an LLM to maintain a structured markdown wiki between
raw sources and later questions. It differs from ordinary retrieval because the
agent does not merely find chunks on demand; it incrementally updates a durable
knowledge layer.

## Why It Matters

The pattern addresses a weakness in RAG-style workflows: the system often has to
rediscover and resynthesize the same evidence for every question. A maintained
wiki preserves prior synthesis, links, and caveats so the next query can build
from already-organized knowledge.

## Components

- Immutable source layer: `raw/`
- Maintained wiki layer: `wiki/`
- Agent instruction layer: [[AGENTS]]

## Related

- [[LLM Wiki]]
- [[Compounding Knowledge Base]]
- [[Wiki Ingest Workflow]]
- [[Wiki Query Workflow]]
