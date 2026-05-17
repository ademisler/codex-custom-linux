# Publishing Checklist

Use this before creating a public GitHub repository.

## Cleanliness

```bash
make scan
```

Expected result: no matches.

## Syntax

```bash
bash -n scripts/*.sh scripts/lib/*.sh
node --check bridges/*.mjs
```

## Recommended First Commit

```bash
git init
git add .
git status
git commit -m "Initial Codex Custom Linux starter kit"
```

## Suggested GitHub Description

Create isolated custom Codex Desktop apps on Linux with provider bridges,
MiniMax M2.7 example config, custom icons, and local automations.

## Suggested Topics

```text
codex
codex-app
linux
electron
minimax
openai-compatible
responses-api
mcp
automation
```
