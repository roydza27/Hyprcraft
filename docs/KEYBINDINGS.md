# Keybindings

Hyprland is the source of truth for window and workspace shortcuts. Shell actions may be triggered from binds, but the compositor must remain usable if Quickshell is stopped.

## Proposed default contract

The exact key choices are not frozen yet. The initial configuration should cover:

- Application launch and terminal
- Close, fullscreen and floating window actions
- Focus and move windows directionally
- Workspace selection and moving windows between workspaces
- Monitor focus and movement
- Reload configuration and restart shell
- Lock and session exit

## Compatibility

The project should preserve familiar Hyprland workflows where practical. Before finalizing defaults, compare them against the existing keybindings contributed by the project maintainer and document intentional changes.

## Contributing bindings

Every binding should have a clear action name, avoid accidental collisions, and be grouped by purpose in the source configuration. Shell-specific binds must have a safe fallback or be explicitly marked optional.
