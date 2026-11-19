# Hyprland configuration

This directory will contain the compositor configuration.

## Ownership

- Window and workspace behavior
- Keyboard bindings
- Monitor rules and environment variables
- Compositor-level animations and effects
- Startup of essential session services

Keep shell UI implementation out of this directory. A binding may invoke a shell action, but core window management must work without Quickshell.
