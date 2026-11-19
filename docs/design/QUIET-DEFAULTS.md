# Quiet interaction defaults

> Status: proposed defaults for prototyping and community feedback. These are not yet implemented or finalized.

Hyprcraft should make useful controls easy to reach without keeping them permanently visible. Automatic behavior must remain transparent, predictable and reversible.

## Desktop bar: auto-hide

**Proposed default:** the primary Quickshell bar auto-hides.

Intent:
- Preserve vertical screen space during focused work.
- Keep essential status information available on demand.
- Avoid turning the bar into a dashboard or widget shelf.

Prototype behavior:
- Reveal the bar when the pointer reaches its configured screen edge or when the user invokes its keyboard shortcut.
- Hide it after the pointer leaves and a short, configurable delay, unless the user is interacting with it.
- Do not let the bar cover important window controls or interfere with edge gestures.
- Keep a manual pin/visibility override available.
- Make the reveal target discoverable without leaving a permanently visible handle.

Open questions:
- Which edge should reveal the bar by default?
- What delay feels responsive without being distracting?
- Should the bar reveal on every workspace or be configurable per monitor?
- Which status items genuinely deserve a place in the minimal bar?

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
