# Development

## Current phase: foundation

Build a small, reliable and quiet baseline before adding features. Hyprcraft is intended to become a community project; the initial implementation is a seed for collaboration, not a finished personal desktop.

## Suggested setup

Target environment: Arch Linux with Hyprland. The required package list will be maintained once the first baseline is tested.

Useful tools:

- Git
- Hyprland
- Quickshell
- Waybar for fallback validation
- QML-capable editor or language server
- ShellCheck for shell scripts

## Working rules

1. Make one focused change at a time.
2. Keep core keybindings usable when the shell is stopped.
3. Prefer minimal defaults; make additional features opt-in.
4. Explain the user problem before proposing a new widget or persistent UI element.
5. Test on a real Hyprland session where possible.
6. Record tested versions and known limitations.
7. Do not commit personal monitor layouts, device IDs, credentials or absolute home-directory paths.

## Community contributions

Open an issue before substantial or architecture-changing work so the problem and approach can be discussed. Small fixes and documentation improvements can go directly to a pull request. Be respectful of differing workflows and hardware constraints.

## Validation checklist

- [ ] Hyprland config parses and starts.
- [ ] Core keybindings work without Quickshell.
- [ ] Quickshell starts and can be restarted independently.
- [ ] Waybar fallback starts without Quickshell.
- [ ] Missing optional dependencies do not crash the session.
- [ ] Existing user configuration is backed up before installation changes.

## Pull requests

Include the motivation, affected components, dependencies, validation performed and what remains untested. For UI changes, include a screenshot and explain why the element belongs in the default experience rather than an optional module.
