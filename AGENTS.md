# Repository Guidelines

## Project Structure & Module Organization
This repository is a Zed editor configuration set. The root contains the user-facing config files and supporting tooling:
- `settings.json` — primary Zed configuration (JSONC with comments).
- `keymap.json` — custom keybindings layered on the VS Code base map.
- `tasks.json` — Zed tasks (e.g., Biome JSON formatting).
- `biome.json` — Biome formatter/linter configuration.
- `themes/` — custom themes.
- `prompts/` and `conversations/` — prompt and chat artifacts.
- `package.json` and `pnpm-lock.yaml` — pin Biome tooling used by tasks.

## Build, Test, and Development Commands
This repo is configuration-focused; there is no build step. Key commands:
- `pnpm install` — install Biome locally so tasks can run.
- `pnpm run check` — run `biome check --write --unsafe` to format and apply safe/unsafe fixes.

## Coding Style & Naming Conventions
- Indentation: 2 spaces (per `biome.json`).
- JSONC: `settings.json` and `keymap.json` allow comments and trailing commas.
- Formatting: use Biome for JSON/JSONC formatting and key sorting; prefer `pnpm run check`.
- Naming: keep file names lowercase with dashes or dots as already used; preserve existing Zed file names.

## Testing Guidelines
No automated tests are defined. Validate changes by:
- Running `pnpm run check`.
- Opening Zed and confirming settings, keymaps, themes, and tasks load as expected.

## Commit & Pull Request Guidelines
There is no Git history yet, so no established commit format. Suggested baseline:
- Short, imperative subject lines (e.g., “Add biome task for JSON sorting”).
- Scope commits to one logical change.
For PRs, include:
- A clear summary of changes and affected files (e.g., `settings.json`, `themes/`).
- Screenshots for visual/theme changes.
- Any Zed tasks or commands needed to verify.

## Security & Configuration Tips
- Keep API keys or tokens out of `settings.json`; prefer Zed’s secure storage if needed.
- Avoid committing machine-specific paths unless intentionally shared.
