# Publishing Checklist

Use this before creating a public GitHub repository.

## Cleanliness

```bash
make scan
```

Expected result: no matches.

## Ownership

Present the project as an open-source starter kit created and maintained by Adem
İşler. Keep the author line, MIT license, security policy, contribution guide,
and public repository metadata consistent.

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

Open-source starter kit by Adem İşler for isolated custom Codex Desktop apps on
Linux, with provider bridges, MiniMax M2.7 config, custom icons, and local
automations.

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
