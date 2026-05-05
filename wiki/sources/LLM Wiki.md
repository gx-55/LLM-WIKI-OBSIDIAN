---
title: LLM Wiki
type: synthesis
tags: [llm-wiki, knowledge-management, obsidian]
sources:
  - "[[raw/clippings/2026-05-04-llm-wiki]]"
created: 2026-05-04
updated: 2026-05-04
---

# LLM Wiki

[[Andrej Karpathy]] describes the [[LLM Wiki Pattern]] as a way to turn a pile
of raw documents into a maintained, interlinked knowledge base. The main move is
to stop treating every question as a fresh retrieval problem. Instead, each new
source is ingested into a persistent wiki where summaries, contradictions,
cross-references, and syntheses are kept current.

## Core Claim

A wiki maintained by an LLM can become a [[Compounding Knowledge Base]] because
the labor of bookkeeping becomes cheap. The agent can update multiple pages in a
single pass, keep links fresh, and preserve prior synthesis so that future
queries start from organized knowledge rather than isolated raw chunks.

## Architecture

- Raw sources are immutable source material.
- The wiki is the LLM-owned working layer: summaries, concepts, entities,
  comparisons, and syntheses.
- The schema is the operating manual, such as [[AGENTS]], that tells the agent
  how to maintain the vault.

## Operations

- [[Wiki Ingest Workflow]] turns a new source into raw metadata, source summary,
  concept updates, entity updates, and index changes.
- [[Wiki Query Workflow]] searches the wiki first and can save valuable answers
  back into the knowledge base.
- Periodic linting checks for contradictions, stale claims, missing links,
  orphan pages, and gaps worth researching.

## Notes

The gist intentionally stays abstract. Its value is the pattern: raw material is
curated by the human, while the LLM performs the maintenance work that makes a
long-lived knowledge base usable.
