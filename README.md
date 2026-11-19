# Hyprcraft

**A modular, keyboard-first desktop for Hyprland.**

Hyprcraft is a community-maintained desktop configuration project for building a cohesive, beautiful and practical Wayland experience. It combines a carefully structured Hyprland setup with a primary [Quickshell](https://quickshell.org/) shell and a [Waybar](https://github.com/Alexays/Waybar) fallback.

> **Project status:** Foundation stage. Interfaces, configuration contracts and installation behavior are being established. Nothing here should be treated as a stable release yet.

## Goals

- **Modular:** components can be enabled, replaced or used independently.
- **Keyboard-first:** predictable shortcuts and efficient window/workspace workflows.
- **Designed, not decorated:** clear hierarchy, deliberate spacing, restrained motion and consistent visual language.
- **Reproducible:** documented dependencies, explicit defaults and repeatable setup.
- **Safe to try:** installation must back up existing configuration and support recovery.
- **Community-maintained:** readable structure, contribution guidance and reviewable changes.

## Initial platform

- Target: Arch Linux
- Compositor: Hyprland
- Primary shell: Quickshell
- Fallback bar: Waybar
- Configuration: Hyprland config + QML + shell scripts

Other distributions may be considered after the Arch experience is reliable.

## Repository layout

```text
config/
  hypr/          compositor configuration
  quickshell/    primary desktop shell
  waybar/        fallback status bar
  launcher/      application launcher integration
  notifications/ notification daemon configuration
  lockscreen/    lock and idle configuration
themes/          visual themes and shared assets
presets/         curated configuration profiles
scripts/         install, backup, restore and validation tools
docs/            architecture, design and contributor docs
```

See [Architecture](docs/ARCHITECTURE.md) for component boundaries and [Development](docs/DEVELOPMENT.md) to get involved.

## Principles

1. Hyprland owns window management, workspaces, binds and compositor behavior.
2. Quickshell owns the primary desktop UI; it must not become a hidden dependency for core window management.
3. Waybar is a fallback, not a second competing source of desktop state.
4. Shared design decisions belong in documented tokens and component guidelines.
5. Scripts must explain what they change; destructive actions require explicit confirmation.
6. User configuration is never silently overwritten.

## Status

Hyprcraft is not ready for one-command installation. The first milestone is a minimal, working baseline with documented keybindings and a shell that can be started and restarted independently.

## Contributing

Read [Development](docs/DEVELOPMENT.md) before opening a pull request. Small, focused contributions are preferred.

## License

No license has been selected yet. Until one is added, the repository is not granting blanket permission to reuse, modify or redistribute its contents.
