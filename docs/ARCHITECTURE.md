# Architecture

## Overview

Hyprcraft is a set of cooperating desktop components, not a monolithic desktop environment. Each component has a clear owner and can fail or be replaced without taking down core window management.

## Component ownership

| Component | Owns | Must not own |
|---|---|---|
| Hyprland | Windows, workspaces, binds, monitor rules, compositor effects | Desktop panels and application widgets |
| Quickshell | Primary bar, launcher surfaces, notifications UI integrations, widgets and shell services | Required window-management logic |
| Waybar | Minimal fallback bar and status modules | A parallel implementation of the full Quickshell shell |
| Supporting tools | Locking, idle, notifications, wallpaper and screenshots | Duplicated policy that conflicts with another component |

## Directory map

- `config/hypr/`: compositor configuration and keyboard workflows.
- `config/quickshell/`: QML entry point, components, services and shell surfaces.
- `config/waybar/`: optional fallback configuration.
- `config/launcher/`: launcher configuration and integration.
- `config/notifications/`: notification daemon configuration.
- `config/lockscreen/`: lock and idle configuration.
- `themes/`: semantic design tokens, theme values and assets.
- `presets/`: curated combinations of supported modules.
- `scripts/`: setup, backup, restore and validation utilities.
- `docs/`: architecture, design and contributor documentation.

## Runtime expectations

- Hyprland starts independently of the shell.
- Quickshell can be restarted without restarting Hyprland.
- A user can choose the Waybar fallback when Quickshell is unavailable.
- Optional integrations must degrade gracefully when their programs or services are absent.
- Machine-specific values (monitor names, paths, device identifiers) must be isolated from shared defaults.

## Configuration strategy

Keep shared defaults in the repository and machine-specific overrides separate. Avoid writing directly into a user's home directory during development. The installer will eventually stage files, back up conflicts and only then activate the selected configuration.

## Current state

This document describes intended boundaries. The implementation is still at the foundation stage; interfaces and startup behavior will be documented as they become real and tested.
