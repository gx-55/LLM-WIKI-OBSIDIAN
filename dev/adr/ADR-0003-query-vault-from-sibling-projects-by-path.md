---
title: Query vault from sibling projects by path
type: adr
status: proposed
decision-date: 2026-05-05
deciders: [me, Codex]
tags: [cross-project-query, agent-workflow, vault-access, knowledge-management]
supersedes: []
superseded-by: []
---

# ADR-0003: Query vault from sibling projects by path

## Context

ADR-0002 decided that the vault should remain a private Git-backed repository
and should not be copied, submoduled, or deployed to a VPS until a concrete need
appears. The next operational question is how an agent working inside another
code project should consult the vault during implementation.

The likely local layout is:

```text
~/vault
~/projects/project-a
~/projects/project-b
```

An agent in `~/projects/project-a` needs read access to prior knowledge such as
[[Wiki Query Workflow]], ADRs, concepts, and raw source summaries. It should not
silently edit `~/vault` while working in a project repository, because that
would mix two different work contexts and make review harder.

Known constraints:
- The vault is the source of accumulated knowledge, not a project dependency.
- Project repositories should not vendor, copy, or submodule the vault.
- Query answers should cite vault files so the source of the knowledge is clear.
- Writes back to the vault should be explicit, reviewed, and usually performed
  from a vault session.

## Decision

We will query the vault from other code projects by absolute or home-relative
path, treating `~/vault` as a read-only sibling knowledge base by default; agents
may read `~/vault/wiki/`, `~/vault/dev/`, and, when needed, `~/vault/raw/`, but
must not edit the vault from a project session unless explicitly asked.

## Consequences

### Positive

- Project agents can consult the knowledge base without duplicating it.
- Git histories stay separate: project changes remain in the project, vault
  changes remain in the vault.
- The workflow keeps the [[File Over App]] property: the knowledge base is still
  just files on disk.
- The same pattern works across local agents, Codex sessions, and future tools
  that can read local files.

### Negative / trade-offs

- Each project needs a small local convention or command that tells the agent
  where the vault is.
- The agent may miss relevant knowledge if the query command is too lexical or
  if terms differ between the project and the vault.
- Cross-project queries are read-only by default, so useful findings may not
  automatically become new wiki pages or ADR updates.

### Neutral

- A future MCP server, local search daemon, or VPS API can wrap the same vault
  later without changing the file-first source of truth.
- This decision works best while the vault is small to medium sized; larger
  scale may require an index.
- A project can keep its own ADRs while still linking to vault concepts.

## Alternatives considered

- Copy relevant wiki pages into each project. Rejected because copies drift and
  weaken the [[Compounding Knowledge Base]].
- Add `~/vault` as a submodule in every project. Rejected because it complicates
  project setup and makes personal knowledge look like a code dependency.
- Query the remote GitHub repository directly. Rejected for normal use because
  local files are faster, private, and available offline after clone.
- Deploy a VPS query API now. Rejected for now because ADR-0002 already defers
  network services until always-on query or automation is needed.
- Allow project agents to freely edit the vault. Rejected because it blurs
  review boundaries and could bypass [[Agent Safety Layers]].

## Implementation sketch

Install a global Codex command:

```text
/Users/rogersxie/.codex/commands/vault-query.md
```

The versioned source of that command lives in this vault:

```text
.codex/commands/vault-query.md
```

Each project can also add a small command or agent instruction:

```markdown
Before architecture or implementation decisions, search `~/vault/wiki/` first,
then `~/vault/dev/`, then `~/vault/raw/` only if needed. Cite consulted files.
Treat `~/vault` as read-only unless the user explicitly asks to update it.
```

For Codex-style usage, the user can also ask directly:

```text
Before implementing this, query ~/vault for related concepts, ADRs, and prior
decisions. Cite the vault files you used.
```

## References

- [[ADR-0002]]
- [[Wiki Query Workflow]]
- [[Agent Slash Commands]]
- [[Cross Project Vault Query]]
- [[Agent Safety Layers]]
- [[File Over App]]
- [[Compounding Knowledge Base]]
