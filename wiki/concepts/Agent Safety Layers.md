---
title: Agent Safety Layers
type: concept
tags: [agent-safety, prompt-injection, version-control]
sources:
  - "[[raw/clippings/2026-05-05-personal-harness-llm-wiki-developer-second-brain]]"
created: 2026-05-05
updated: 2026-05-05
---

# Agent Safety Layers

Agent Safety Layers are overlapping controls that reduce the risk of an agent
damaging or leaking a vault. In the [[Personal LLM Harness]], the safety model
is deliberately simple: clear zone rules, limited tools, plan-before-write
gates, git history, and human review.

## Layers

- Zone policy from [[Vault Zone Separation]]
- No-delete rules in [[AGENTS]]
- Slash command tool allowlists
- Plan-before-write for ingest and broad edits
- Git diffs and frequent commits
- Skepticism toward instructions embedded inside external sources

## Prompt Injection

External sources can contain instructions that conflict with the user's rules.
The harness treats source content as data to analyze, not commands to obey. This
is especially important for [[Wiki Ingest Workflow]].

## Related

- [[Agent Slash Commands]]
- [[File Over App]]
- [[Durable Digital Artifacts]]
