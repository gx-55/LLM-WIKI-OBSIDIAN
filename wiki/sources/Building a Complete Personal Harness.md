---
title: Building a Complete Personal Harness
type: synthesis
tags: [llm-wiki, second-brain, obsidian, developer-workflow]
sources:
  - "[[raw/clippings/2026-05-05-personal-harness-llm-wiki-developer-second-brain]]"
created: 2026-05-05
updated: 2026-05-05
---

# Building a Complete Personal Harness

[[Roan Brasil Monteiro]] describes a concrete [[Personal LLM Harness]] for
Obsidian that combines the [[LLM Wiki Pattern]] with a [[Developer Second Brain]].
The article's practical claim is that developers should not keep reading
synthesis and engineering decisions in separate systems. ADRs, debriefs,
projects, and technical notes should live beside the wiki, but under different
rules.

## Core Architecture

The harness uses [[Vault Zone Separation]]:

- `raw/` is immutable curated input.
- `wiki/` is agent-maintained synthesis.
- `dev/` is collaborative developer work.
- The schema layer, such as [[AGENTS]], defines the agent's operating policy.

## Recommended Path

The article recommends direct filesystem access with Obsidian skills as the
starting point. This keeps the setup simple, portable, and aligned with
[[File Over App]]. MCP-based Obsidian access is useful later when the agent needs
plugin-specific operations such as Dataview queries or palette commands.

## Operational Pattern

[[Agent Slash Commands]] turn recurring workflows such as ingest and query into
repeatable operations. [[Agent Safety Layers]] keep those operations bounded:
tool allowlists, plan-before-write gates, git diffs, and explicit no-delete
rules.

## Related

- [[LLM Wiki Pattern]]
- [[Wiki Ingest Workflow]]
- [[Wiki Query Workflow]]
- [[Daily Note Synthesis]]
