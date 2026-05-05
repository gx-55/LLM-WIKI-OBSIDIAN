---
description: Query the personal vault from any project without editing it
argument-hint: <question in natural language>
allowed-tools: Bash(rg:*), Bash(find:*), Bash(sed:*), Bash(cat:*)
---

Answer **$ARGUMENTS** by consulting the personal vault at `/Users/rogersxie/vault`.

Treat the vault as read-only unless the user explicitly asks to update it.

## Search order

1. Search `/Users/rogersxie/vault/wiki/` first.
2. If needed, search `/Users/rogersxie/vault/dev/` for ADRs, debriefs, projects, and snippets.
3. Read `/Users/rogersxie/vault/raw/` only when source-level evidence is needed.

## Process

1. Use `rg` to find candidate files. Prefer title, tag, heading, and wikilink matches.
2. Read focused sections from the most relevant files. Do not read the entire vault.
3. Synthesize the answer in the current project context.
4. Cite consulted vault files using Obsidian wikilinks when clear, and include paths when the project context needs exact files.

## Rules

- Do not edit `/Users/rogersxie/vault` from another project session unless explicitly asked.
- Do not copy vault pages into the current project.
- Do not add the vault as a project dependency.
- If the vault lacks enough information, say so directly.
- If the answer is an inference, mark it as inference and name the files it is based on.

## Useful searches

```bash
rg -n "<term>" /Users/rogersxie/vault/wiki /Users/rogersxie/vault/dev
rg -n "\[\[.*<term>.*\]\]" /Users/rogersxie/vault/wiki /Users/rogersxie/vault/dev
find /Users/rogersxie/vault/wiki /Users/rogersxie/vault/dev -name "*.md"
```
