# Custom Apps

A custom Codex app is a side-by-side clone with its own identity and runtime
state.

## Create One

```bash
./scripts/create-custom-codex-app.sh \
  --id codex-acme \
  --name "Codex Acme" \
  --home "$HOME/.codex-acme" \
  --port 5180 \
  --icon-color "#dc2626"
```

Generated paths:

```text
~/.local/opt/codex-acme/codex-app
~/.local/share/applications/codex-acme.desktop
~/.codex-acme
```

The generated desktop entry points to:

```text
~/.local/bin/codex-acme-desktop
```

The shell creator writes a generic wrapper. Provider-specific installers can
replace it with a wrapper that starts the bridge, loads the custom environment,
and points Codex at the isolated `CODEX_HOME`.

## App Identity

Use a unique app id for every custom app:

- App id: `codex-minimax`
- Desktop file: `codex-minimax.desktop`
- Webview port: `5176`
- `CODEX_HOME`: `~/.codex-minimax`
- Taskbar class: `codex-minimax`

Reusing the same id or port causes the confusing behavior this project is meant
to prevent.

## Updating After Base App Changes

When the base Codex app updates, recreate the custom shell:

```bash
./scripts/create-custom-codex-app.sh \
  --id codex-minimax \
  --name "Codex MiniMax" \
  --port 5176 \
  --icon-color "#ef4444" \
  --replace
```

The custom `CODEX_HOME` remains separate and is not deleted.
