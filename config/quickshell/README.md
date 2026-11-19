# Quickshell

Quickshell is the primary desktop shell and presentation layer.

## Planned structure

```text
quickshell/
  shell/       entry point and root shell
  components/  reusable visual components
  panels/      minimal bar and overview surfaces
  services/    compositor and system integrations
  README.md
```

## Primary experience: desktop overview

The Super key opens the full-screen desktop overview. It is the central place to inspect open windows, navigate workspaces and search installed applications.

Read [Desktop Overview](../../docs/design/OVERVIEW.md) before implementing overview behavior.

## Minimal bar

The default Quickshell bar is proposed to auto-hide from the top edge. It contains only workspace state, clock/date and essential system indicators. It must not become a dashboard.

Read [Minimal desktop bar](../../docs/design/BAR.md) before implementing bar behavior.

## Responsibilities

- Render the on-demand overview and window previews.
- Render the minimal auto-hiding bar.
- Present workspace navigation.
- Provide integrated application search and browsing.
- Keep persistent desktop UI minimal.
- Separate system state from presentation.

## Boundaries

- Hyprland remains the source of truth for windows, workspaces, focus and window movement.
- Quickshell must not become a dependency for core window management.
- The overview must be inexpensive while closed and must not continuously animate or poll unnecessarily.
- The bar must be idle while hidden and must not steal focus when revealed.
- The shell must be restartable without restarting Hyprland.
- Optional surfaces and providers must be independently disableable.

Keep QML components small and reusable. Do not implement speculative features before the overview and bar interactions are validated.
