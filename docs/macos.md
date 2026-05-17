# macOS Local Profile

The Linux installer is the primary target of this repository, but the same
provider bridge can be used on macOS without modifying the original Codex app.

The macOS installer creates a separate app bundle and a separate `CODEX_HOME`:

```text
~/Applications/Codex MiniMax.app
~/.codex-minimax
~/.local/bin/codex-minimax
~/.local/bin/codex-minimax-desktop
~/.local/bin/codex-minimax-proxy
```

It copies `/Applications/Codex.app` into your user Applications folder, patches
only the copied bundle, and launches it with isolated environment variables.
The original `/Applications/Codex.app` and your normal `~/.codex` profile are
left untouched.

## Install

```bash
export MINIMAX_API_KEY="<your-minimax-api-key>"

./scripts/install-minimax-profile-macos.sh \
  --id codex-minimax \
  --name "Codex MiniMax" \
  --model "MiniMax-M2.7" \
  --port 4007 \
  --webview-port 5176
```

If you do not export `MINIMAX_API_KEY`, the installer still creates the profile.
Edit this private file before testing the provider:

```text
~/.codex-minimax/minimax.env
```

## Test

```bash
codex-minimax-proxy start
codex-minimax-proxy test
open -n "$HOME/Applications/Codex MiniMax.app"
```

## Remove

```bash
codex-minimax-proxy stop
codex-minimax-proxy automations-stop
rm -rf "$HOME/Applications/Codex MiniMax.app"
rm -f "$HOME/.local/bin/codex-minimax" \
  "$HOME/.local/bin/codex-minimax-desktop" \
  "$HOME/.local/bin/codex-minimax-proxy"
```

The custom `CODEX_HOME` is kept by default. Remove `~/.codex-minimax` only if
you also want to delete the custom profile data.
