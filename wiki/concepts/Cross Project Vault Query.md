---
title: Cross Project Vault Query
type: concept
tags: [cross-project-query, agent-workflow, vault-access]
sources:
  - "[[ADR-0003]]"
created: 2026-05-05
updated: 2026-05-05
---

# Cross Project Vault Query

Cross Project Vault Query is the workflow for letting an agent inside another
code project consult this vault without making the vault a dependency of that
project. It implements [[ADR-0003]] by treating `/Users/rogersxie/vault` as a
read-only sibling knowledge base.

## Command

The global Codex command is:

```text
/vault-query <question>
```

It is installed at:

```text
/Users/rogersxie/.codex/commands/vault-query.md
```

A versioned copy lives in this vault at:

```text
.codex/commands/vault-query.md
```

## Behavior

The command searches `wiki/` first, then `dev/`, then `raw/` only when source
evidence is needed. It cites consulted files and keeps vault writes explicit.

## Related

- [[Agent Slash Commands]]
- [[Wiki Query Workflow]]
- [[Agent Safety Layers]]
- [[Personal LLM Harness]]
