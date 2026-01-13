# Zed Config

This repo contains user-level configuration for the Zed editor. It’s focused on JSON/JSONC formatting with Biome via [Zed Tasks](https://zed.dev/docs/tasks), a VS Code–style keymap baseline, a VS Code inspired theme, and a few productivity-focused defaults.

## What’s here

- `settings.json`: Main Zed settings (editor behavior, language tooling, UI, themes, agent config).
- `keymap.json`: Custom key bindings on top of the base keymap.
- `tasks.json`: Zed task entries (e.g., JSON sorting via Biome).
- `biome.json`: Biome formatter/linter configuration used by tasks and LSP.
- `package.json` + `pnpm-lock.yaml`: Pin Biome tooling via pnpm.

## Implemented features

### Agent + assistant
- Default agent model set to `gpt-4o` with the OpenAI provider.
- Inline assistant model set to `gpt-5-mini` with the OpenAI provider.
- No custom model parameters configured yet.

### Editor + UI + Theme
- Base keymap: **VSCode**.
- Fonts: UI font size 16; buffer font size 14.
- Theme: Dark mode with “Dark (Visual Studio)” and light fallback “One Light”.
- Bracket colorization enabled; indent guides are indent-aware with background coloring disabled.
- Sticky scroll enabled.
- Document color previews shown as **background**.
- Edit predictions enabled using Zed’s built-in provider.
- Tab size set to 2.

### Language tooling
- Biome is the formatter for JavaScript, TypeScript, TSX, and JSONC.
- On format, Biome fixes are applied via `source.fixAll.biome` for those languages.
- TypeScript uses `tsgo` and `vtsls` language servers.
- Biome LSP requires a config file (ensures repo-level config is honored).

### Tasks
- “Sort JSON (current file)” task runs Biome with `--write --unsafe` on the current file and uses the repo’s `biome.json`.

### Biome formatting rules
- Sorted keys enabled via assist actions.
- JSON parser allows comments and trailing commas (JSONC support).
- Formatter uses 2-space indentation and trailing commas.
- Linting enabled; VCS integration disabled.

## Notes
- `keymap.json` and `settings.json` use comments (JSONC style), so JSON tooling must allow comments to parse them.
- The task runs Biome via pnpm in this repo, so `node_modules` needs to be installed for the task to work.
