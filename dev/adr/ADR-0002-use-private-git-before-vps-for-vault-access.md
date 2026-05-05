---
title: Use private Git before VPS for vault access
type: adr
status: proposed
decision-date: 2026-05-05
deciders: [me, Codex]
tags: [vault-sync, git, vps, cross-project-query, knowledge-management]
supersedes: []
superseded-by: []
---

# ADR-0002: Use private Git before VPS for vault access

## Context

ADR-0001 established the vault as a file-first, LLM-maintained knowledge base.
The next design question is how this knowledge base should be migrated between
machines and queried from other code projects without weakening the file-first
model.

The current vault works best when the agent operates inside `~/vault`, but real
developer work happens across sibling repositories such as `~/projects/project-a`
and `~/projects/project-b`. Those projects need a way to consult prior
knowledge, ADRs, and wiki concepts without copying the vault into each project
or mixing Git histories.

The vault is also private by nature. It contains source notes, decisions,
synthesis, and possibly daily notes. [[Agent Safety Layers]] and [[File Over App]]
both point toward a conservative approach: keep the primary artifact as private,
versioned files, and add network services only when they solve a concrete
problem.

## Decision

We will use a private Git remote as the first migration and sync mechanism, keep
the vault as a sibling repository to code projects, and defer VPS deployment
until always-on search, automation, or API access is actually needed.

## Consequences

### Positive

- Migration to another laptop stays simple: clone the private repository into
  `~/vault`.
- Other code projects can query the vault by path without embedding the vault in
  each project.
- The vault keeps a clean Git history and remains aligned with [[File Over App]]
  and [[Durable Digital Artifacts]].
- A private Git remote gives backup and portability without exposing a new
  network service.

### Negative / trade-offs

- Querying from another project still depends on agents or commands being told
  where `~/vault` lives.
- File search and `wiki/index.md` may become weak when the vault grows beyond
  the current scale.
- No always-on web UI or API exists yet.
- Multi-machine edits require ordinary Git hygiene: pull before editing, commit
  coherent changes, and resolve conflicts when they happen.

### Neutral

- A VPS remains an option for future search, scheduled synthesis, private APIs,
  or self-hosted Git.
- This decision does not require Obsidian to be open.
- This decision does not prevent adding a local search index or embeddings
  later.

## Alternatives considered

- Deploy the vault to a VPS now. Rejected for now because it adds operational
  and security surface before there is a proven need for always-on access.
- Copy the vault into each code project. Rejected because it duplicates private
  knowledge, creates sync problems, and mixes unrelated Git histories.
- Add the vault as a submodule to every project. Rejected because it makes
  project setup more complex and treats personal knowledge as project-local
  dependency plumbing.
- Use only local files with no remote. Rejected because migration, backup, and
  recovery are weaker without a private remote.

## References

- [[ADR-0001]]
- [[Personal LLM Harness]]
- [[Agent Slash Commands]]
- [[Agent Safety Layers]]
- [[File Over App]]
- [[Durable Digital Artifacts]]
- [[Wiki Query Workflow]]
