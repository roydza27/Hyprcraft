# Quiet interaction defaults

> Status: proposed defaults for prototyping and community feedback. These are not yet implemented or finalized.

Hyprcraft should make useful controls easy to reach without keeping them permanently visible. Automatic behavior must remain transparent, predictable and reversible.

## Desktop bar: auto-hide

**Proposed default:** a top-edge Quickshell bar that auto-hides.

- Reveal on pointer arrival at a small, invisible top-edge activation strip.
- Provide a keyboard shortcut as an alternative; choose the chord only after checking the full Hyprland key map and avoiding the Super-key overview.
- Hide after the pointer leaves and a short configurable delay, unless the user is interacting with the bar or one of its menus.
- Begin testing around a 500 ms hide delay; treat it as a prototype value, not a final standard.
- Provide a manual pin-visible override.
- Do not leave a visible handle or permanent panel while hidden.

The default information groups are workspace state, clock/date, and essential system status (battery when present, network, audio and a notification indicator). No weather, news, CPU/RAM graphs, music controls or decorative widgets by default.

See [Minimal desktop bar](BAR.md) for placement, interaction, multi-monitor behavior, performance requirements and acceptance checks.

## Focus mode: automatic

**Proposed default:** focus mode activates automatically when an explicit user-configured context rule matches.

Focus mode should reduce interruptions, not take control away from the user.

Candidate rule signals for experiments:
- A selected workspace.
- A foreground application or application class.
- A user-defined schedule.

No application list, workspace mapping or schedule should be hard-coded as a universal default before community testing.

Behavior requirements:
- Show a subtle, understandable indication when focus mode is active.
- Suppress nonessential notifications while preserving critical/system alerts and user-defined exceptions.
- Allow immediate manual activation, deactivation and temporary pause.
- Explain which rule activated focus mode.
- Avoid repeated state changes when switching rapidly between windows.
- Use compositor or application events where possible; do not add a high-frequency polling loop.

Open questions:
- Which context signals are reliable and privacy-respecting?
- Should manual override last until the next context change, for a fixed duration, or until explicitly reset?
- Which notification categories must always bypass focus mode?
- Should schedules be part of the first version or a later optional module?

## Resource and accessibility requirements

- Auto-hide must not mean a permanently running animation.
- Hidden UI should not continuously render or poll.
- Focus rules should be evaluated on relevant state changes, not by constant polling.
- Users must be able to disable automatic focus behavior.
- Provide reduced-motion behavior and a keyboard-only path to reveal and control the bar.
- The fallback Waybar profile should remain usable even if Quickshell is unavailable.

## Prototype acceptance checks

Before adopting these defaults as stable:
1. Verify the bar can be revealed reliably with keyboard and pointer.
2. Verify it does not appear unexpectedly during normal window interaction.
3. Verify focus rules are visible, understandable and easy to override.
4. Verify critical notifications are not silently lost.
5. Measure idle CPU and memory with the bar hidden and focus mode idle.
6. Test multiple monitors, scaling, edge gestures and reduced motion.
7. Gather feedback from users with different workflows before fixing the defaults.

Related: [Design principles](PRINCIPLES.md), [Architecture](../ARCHITECTURE.md), [Performance](../PERFORMANCE.md).
