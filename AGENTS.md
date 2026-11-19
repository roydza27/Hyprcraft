# Repository guide for coding agents

## Project intent

Hyprcraft is a modular, keyboard-first Hyprland desktop configuration for Arch Linux. Quickshell is the primary shell; Waybar is the fallback.

## Non-negotiable boundaries

- Keep compositor behavior and keybindings in `config/hypr/`.
- Do not make core window management depend on Quickshell.
- Keep Quickshell UI and services under `config/quickshell/`.
- Keep the Waybar fallback independent and intentionally smaller in scope.
- Shared visual decisions must be documented under `docs/design/` before being duplicated across components.
- Do not introduce a theme palette or visual direction without documenting its rationale. Prefer semantic tokens over scattered color literals.
- Do not copy third-party configurations wholesale. Track provenance and respect their licenses.

## Safety

- Never overwrite a user's existing configuration without a backup and explicit confirmation.
- Install and restore scripts must be idempotent where practical, validate inputs, and explain their actions.
- Do not run privileged commands automatically.
- Do not assume a package manager other than pacman in the initial Arch target.
- Do not claim a configuration has been tested unless it was actually run on a supported system.

## Engineering conventions

- Prefer small, composable files over monolithic configuration files.
- Use descriptive names and comments only where they clarify intent.
- Keep dependencies explicit and distinguish required from optional packages.
- Avoid unnecessary frameworks, background services and resource-heavy features.
- Preserve user customizations and make defaults easy to override.

## Before submitting changes

1. Check the relevant documentation and existing conventions.
2. Validate shell scripts with `bash -n` and shellcheck when available.
3. Validate JSON, YAML and QML with suitable tooling when available.
4. Update docs when behavior, dependencies, keybindings or configuration contracts change.
5. Summarize what changed, how it was checked and what remains untested.
