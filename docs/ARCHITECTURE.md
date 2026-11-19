# Architecture

## Overview

Hyprcraft is a set of cooperating desktop components, not a monolithic desktop environment. Each component has a clear owner and can fail or be replaced without taking down core window management.

The default profile should remain small. Optional features must not become mandatory dependencies.

## Component ownership

| Component | Owns | Must not own |
|---|---|---|
| Hyprland | Windows, workspaces, binds, monitor rules, compositor effects | Desktop panels and application widgets |
| Quickshell | Minimal primary bar and on-demand shell surfaces | Required window-management logic |
| Waybar | Small fallback status bar | A parallel implementation of every shell feature |
| Supporting tools | Locking, idle, notifications, wallpaper and screenshots | Duplicated policy that conflicts with another component |

## Default vs optional

The base profile should include only what is needed for a usable session. Dashboards, decorative widgets, elaborate effects, extra panels and integrations belong in optional modules or presets. Optional modules should be independently disableable and should not increase the base dependency set without a clear reason.

## Directory map

- `config/hypr/`: compositor configuration and keyboard workflows.
- `config/quickshell/`: QML entry point, minimal shell surfaces and services.
- `config/waybar/`: optional fallback configuration.
- `config/launcher/`: launcher configuration and integration.
- `config/notifications/`: notification daemon configuration.
- `config/lockscreen/`: lock and idle configuration.
- `themes/`: semantic design tokens and theme values.
- `presets/`: curated optional combinations.
- `scripts/`: setup, backup, restore and validation utilities.
- `docs/`: architecture, design and contributor documentation.

## Runtime expectations

- Hyprland starts independently of the shell.
- Quickshell can be restarted without restarting Hyprland.
- A user can choose Waybar when Quickshell is unavailable.
- Optional integrations degrade gracefully when absent.
- Machine-specific values are isolated from shared defaults.

## Community and extensibility

Prefer stable, documented interfaces over tightly coupled features. New modules should state their dependencies, resource costs, configuration surface and failure behavior. Keep the base profile conservative; let users and community presets add complexity when they need it.

## Current state

This describes intended boundaries. The implementation is still at the foundation stage; interfaces and startup behavior will be documented as they become real and tested.
