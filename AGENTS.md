# Repository guide for coding agents

## Project intent

Hyprcraft is an early, community-shaped Hyprland desktop project for Arch Linux. Its goals are a polished, coherent interface and fast keyboard-driven workflows, with low idle and active memory use as a core requirement. Quickshell is the primary shell; Waybar is the fallback.

This repository is a shared project, not a request to reproduce one maintainer's personal desktop. Do not treat an individual preference as community consensus.

## Product and design boundaries

- Aim for refined typography, spacing, hierarchy and interaction—not visual imitation of proprietary desktops.
- Default to essentials. Every always-visible element must justify its attention, screen space and resource cost.
- Keep optional widgets, visual effects, animations and integrations opt-in and independently disableable.
- Prefer usable space, clear hierarchy, readable status and predictable behavior over decoration.
- Do not add features merely to make the desktop look busy or impressive.
- Keep compositor behavior and keybindings in `config/hypr/`.
- Core window management must work without Quickshell.
- Keep Quickshell UI and services under `config/quickshell/`; keep Waybar fallback intentionally smaller.
- Document shared design decisions under `docs/design/`.
- Do not introduce a palette or visual direction without rationale and community discussion.
- Do not copy third-party configurations wholesale. Track provenance and respect licenses.

## Performance requirements

- Low memory use is a product requirement, not a later optimization.
- Measure idle session memory separately from overview-open and feature-active memory.
- Avoid unnecessary resident processes, duplicate daemons, busy polling, large caches and continuously running animations.
- Prefer event-driven updates and lazy initialization.
- Release or suspend expensive previews and resources when the overview closes.
- Record test hardware, software versions and measurement method; never publish unsupported performance claims.
- Evaluate CPU use, startup time and responsiveness alongside RAM.

## Community practice

- Treat issues and pull requests as collaboration, not implementation orders from a single person.
- For substantial features, establish the user problem and trade-offs before coding.
- Prefer small, reviewable contributions.
- Do not close reasonable alternatives solely because they differ from the initial author's taste.
- Clearly distinguish established project decisions from proposals and experiments.

## Safety

- Never overwrite a user's existing configuration without a backup and explicit confirmation.
- Install and restore scripts must validate inputs and explain their actions.
- Do not run privileged commands automatically.
- Do not claim a configuration has been tested unless it was actually run on a supported system.

## Engineering conventions

- Prefer small, composable files.
- Keep dependencies explicit; distinguish required from optional.
- Avoid unnecessary frameworks, background services and resource-heavy features.
- Preserve user customizations and make defaults easy to override.

## Before submitting changes

1. Check existing documentation and conventions.
2. Validate scripts and configuration with suitable tools where available.
3. Update docs when behavior, dependencies or configuration contracts change.
4. For runtime changes, report resource measurements where possible.
5. Summarize what changed, how it was checked and what remains untested.
