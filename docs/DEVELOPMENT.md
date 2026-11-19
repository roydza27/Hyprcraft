# Development

## Current phase: foundation

The first objective is a small, working baseline—not a large collection of widgets. Establish the configuration contract, a reliable startup path and a clear visual language before expanding features.

## Suggested setup

Target environment: Arch Linux with Hyprland. The exact required package list will be maintained in the dependency manifest once the first baseline is tested.

Useful tools:

- Git
- Hyprland
- Quickshell (primary shell development)
- Waybar (fallback validation)
- A QML-capable editor or language server
- ShellCheck for shell scripts

## Working rules

1. Make one focused change at a time.
2. Keep core keybindings usable when the shell is stopped.
3. Test on a real Hyprland session where possible; static inspection is not runtime validation.
4. Record tested versions and known limitations.
5. Do not commit personal monitor layouts, device IDs, credentials or absolute home-directory paths.

## Validation checklist

- [ ] Hyprland config parses and starts.
- [ ] Core keybindings work without Quickshell.
- [ ] Quickshell starts and can be restarted independently.
- [ ] Waybar fallback starts without Quickshell.
- [ ] Missing optional dependencies do not crash the session.
- [ ] Existing user configuration is backed up before installation changes it.

## Pull requests

Include the motivation, affected components, dependencies, validation performed and screenshots or recordings for visible UI changes. Mark anything not tested.
