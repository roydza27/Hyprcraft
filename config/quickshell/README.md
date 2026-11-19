# Quickshell

Quickshell is the primary desktop shell and presentation layer.

## Planned structure

```text
quickshell/
  shell/       entry point and root shell
  components/  reusable visual components
  panels/      overview and minimal persistent surfaces
  services/    compositor and system integrations
  README.md
```

## Primary experience: desktop overview

The Super key opens the full-screen desktop overview. It is the central place to inspect open windows, navigate workspaces and search installed applications.

Read [Desktop Overview](../../docs/design/OVERVIEW.md) before implementing UI behavior.

## Responsibilities

- Render the overview and window previews.
- Present workspace navigation.
- Provide integrated application search and browsing.
- Keep persistent desktop UI minimal.
- Separate system state from presentation.

## Boundaries

- Hyprland remains the source of truth for windows, workspaces, focus and window movement.
- Quickshell must not become a dependency for core window management.
- The overview must be inexpensive while closed and must not continuously animate or poll unnecessarily.
- The shell must be restartable without restarting Hyprland.
- Optional surfaces and providers must be independently disableable.

Keep QML components small and reusable. Do not implement speculative features before the overview's core interaction is validated.
