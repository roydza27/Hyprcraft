# Quickshell

Quickshell is the primary desktop shell.

Planned structure:

```text
quickshell/
  shell/       entry point and root shell
  components/  reusable visual components
  panels/      bar, launcher and desktop surfaces
  services/    system integrations and state
  README.md
```

Keep QML components small and reusable. Separate system state from presentation, avoid unnecessary polling, and make shell restart independent of Hyprland.
