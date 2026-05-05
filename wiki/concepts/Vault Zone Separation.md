---
title: Vault Zone Separation
type: concept
tags: [vault-architecture, obsidian, agent-policy]
sources:
  - "[[raw/clippings/2026-05-05-personal-harness-llm-wiki-developer-second-brain]]"
created: 2026-05-05
updated: 2026-05-05
---

# Vault Zone Separation

Vault Zone Separation is the practice of giving different folders different
ownership and editing rules. In the [[Personal LLM Harness]], this prevents
source material, agent-maintained synthesis, and collaborative developer work
from drifting into one undifferentiated pile.

## Zones

- `raw/`: human-curated, read-only source material.
- `wiki/`: LLM-maintained concepts, entities, syntheses, and indices.
- `dev/`: collaborative developer artifacts such as ADRs and debriefs.
- Schema layer: [[AGENTS]] or an equivalent root instruction file.

## Why It Works

Folder boundaries make policy concrete. When an agent sees an ambiguous request,
the zone tells it whether it can edit, should ask, or must only read. This is
what turns the vault from a folder of markdown into an operational harness.

## Related

- [[Building a Complete Personal Harness]]
- [[Developer Second Brain]]
- [[Agent Safety Layers]]
- [[LLM Wiki Pattern]]
