# Hyprcraft

**A quiet, modular desktop for Hyprland. Built in the open, shaped by the community.**

Hyprcraft is a community project for creating a practical, keyboard-first Wayland desktop. Its default experience aims to stay out of the way: essential information, deliberate interactions and no unnecessary visual noise.

It starts with Hyprland, Quickshell as the primary shell and Waybar as a lightweight fallback. The project is a shared foundation—not one person's finished desktop or personal aesthetic.

> **Status:** Early foundation. The structure and principles are being established; this is not a stable distribution or ready-to-run installer.

## What we're aiming for

- **Quiet by default:** show only what helps; keep widgets, effects and decoration optional.
- **Keyboard-first:** efficient window and workspace workflows without requiring a busy interface.
- **Modular:** components can be replaced, disabled or used independently.
- **Lightweight:** avoid unnecessary services, polling, animations and resource-heavy effects.
- **Reproducible and safe:** explicit dependencies, backups and a documented recovery path.
- **Community-shaped:** proposals, discussion and contributions should influence the direction.

## Initial platform

- Target: Arch Linux
- Compositor: Hyprland
- Primary shell: Quickshell
- Fallback bar: Waybar

Other distributions may be considered after the Arch baseline is reliable.

## Design direction

Hyprcraft should not demand attention. The default desktop should prioritize usable space, legible status information and predictable behavior. The bar is proposed to auto-hide; focus mode is proposed to activate automatically from transparent, user-configurable context rules. Neither should become difficult to override.

Optional features can be opt-in, independently disableable and justified by a real use case. Minimal does not mean unfinished or difficult to use.

The proposed [Desktop Overview](docs/design/OVERVIEW.md) is the primary navigation interaction. See the [Minimal Desktop Bar](docs/design/BAR.md), [Design Principles](docs/design/PRINCIPLES.md), [Quiet Defaults](docs/design/QUIET-DEFAULTS.md) and [Performance](docs/PERFORMANCE.md).

## Community

Hyprcraft is intended to be built with its users and contributors, not presented as a completed personal creation. The initial repository is a starting point. Defaults, features and visual decisions are open to discussion and review.

- Read [CONTRIBUTING.md](CONTRIBUTING.md) before submitting changes.
- Open an issue to discuss a problem or propose a feature.
- For substantial changes, explain the user need and trade-offs before implementation.
- Credit contributors and respect the licenses of upstream work.

The project does not yet have a formal governance structure. Until one is agreed, maintainers should explain decisions publicly and invite discussion rather than treating personal preference as project consensus.

## Repository layout

```text
config/          compositor and shell configuration
themes/          shared semantic theme values
presets/         curated, optional configurations
scripts/         setup, backup, restore and validation
docs/            architecture, design and contributor documentation
```

## Current milestone

Establish a minimal Hyprland baseline, preserve core keyboard workflows, define the shell boundaries and agree on design principles. Installation tooling and optional features come later.

## License

No license has been selected yet. Until one is added, the repository does not grant blanket permission to reuse, modify or redistribute its contents.
