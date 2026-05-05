---
title: Building a Complete Personal Harness
type: reading
tags: [llm-wiki, second-brain, obsidian, agent-harness]
source-url: https://medium.com/@roanmonteiro/building-a-complete-personal-harness-llm-wiki-developers-second-brain-in-obsidian-d7b61c7398ff
author: Roan Brasil Monteiro
captured: 2026-05-05
---

# Building a Complete Personal Harness

Source record for [[Roan Brasil Monteiro]]'s tutorial on combining the
[[LLM Wiki Pattern]] with a [[Developer Second Brain]] in Obsidian.

## Summary

The article turns the abstract LLM wiki idea into an operational vault setup.
Its central move is to combine two axes in one Obsidian vault: a wiki for
article/book/paper knowledge, and a developer second brain for ADRs, debriefs,
projects, snippets, and technical notes. The author argues that splitting these
into separate vaults loses cross-reference value, while merging them without
physical discipline creates drift.

The proposed architecture uses three content zones plus a schema layer:
`raw/` for immutable curated sources, `wiki/` for agent-maintained synthesis,
`dev/` for collaborative developer artifacts, and a root instruction file that
defines operating rules. The recommended starting path is direct filesystem
access plus Obsidian skills, because it is portable, debuggable, and aligned
with [[File Over App]].

## Key Takeaways

- The useful harness is not just a note app; it is a ruled environment where the
  agent knows what it can read, edit, and create.
- Developers need ADRs, debriefs, projects, snippets, and technical readings in
  the same vault as their synthesized knowledge.
- Physical folder separation makes agent permissions and ambiguity handling
  concrete.
- Direct filesystem access is the recommended starting architecture; MCP should
  be added later only when Obsidian-specific operations are needed.
- Slash commands should be narrow, planned, and tool-limited.
- Git, plan-before-write flows, and limited tool access form defense in depth
  against accidental damage and prompt injection.
- Daily notes belong in `raw/daily/` and can be periodically synthesized rather
  than directly edited by the agent.

## Links

- Source summary: [[Building a Complete Personal Harness]]
- Author: [[Roan Brasil Monteiro]]
- Concepts: [[Personal LLM Harness]], [[Developer Second Brain]], [[Vault Zone Separation]], [[Agent Slash Commands]], [[Agent Safety Layers]], [[Daily Note Synthesis]]
