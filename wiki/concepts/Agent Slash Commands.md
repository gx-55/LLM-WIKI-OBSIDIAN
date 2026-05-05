---
title: Agent Slash Commands
type: concept
tags: [agent-workflow, slash-commands, automation]
sources:
  - "[[raw/clippings/2026-05-05-personal-harness-llm-wiki-developer-second-brain]]"
created: 2026-05-05
updated: 2026-05-05
---

# Agent Slash Commands

Agent Slash Commands are named, repeatable workflows that tell the agent what to
do now. In the [[Personal LLM Harness]], commands such as `/wiki-ingest` and
`/wiki-query` encode operational behavior on top of the broader vault rules.

## Role

Skills describe how the agent should perform a domain-specific task. Slash
commands invoke a concrete operation. This distinction keeps reusable knowledge
separate from one-off execution.

## Safety Pattern

Commands should use narrow tool permissions, present plans before broad writes,
and cite files when answering from the vault. This links [[Agent Slash Commands]]
to [[Agent Safety Layers]].

## Related

- [[Wiki Ingest Workflow]]
- [[Wiki Query Workflow]]
- [[Building a Complete Personal Harness]]
