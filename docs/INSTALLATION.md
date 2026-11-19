# Installation

> Installation is not implemented yet. Do not copy this repository over an existing `~/.config` directory.

## Planned installation flow

1. Detect the operating system and required tools.
2. Check supported versions and dependencies.
3. Show the files and packages that would be changed.
4. Back up conflicting configuration with a timestamp.
5. Install the selected profile.
6. Validate configuration and report next steps.
7. Provide a documented restore path.

## Safety requirements

- No silent overwrite of existing files.
- No automatic privileged commands.
- Dry-run mode before applying changes.
- Clear distinction between required and optional packages.
- Restore must use the backup created by the matching install.
- A failed installation must leave the previous configuration recoverable.

The first installer target will be Arch Linux and pacman. Other distributions are out of scope until the baseline is stable.
