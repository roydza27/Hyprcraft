# Minimal desktop bar

> Status: first interaction blueprint. Proposed for prototyping and community feedback; not implemented or finalized.

## Purpose

The bar is a temporary status surface, not a dashboard. It should make a small set of useful facts available at a glance, then leave the screen to the user's work.

**Proposed default:** a top-edge, auto-hiding bar.

## Placement and reveal

- Place the default bar along the top edge of each configured monitor.
- Reveal it when the pointer reaches a small, invisible activation strip at the top edge.
- Provide a keyboard shortcut as an alternative. The exact chord remains undecided until the full Hyprland key map is reviewed; it must not conflict with the Super-key overview.
- Do not leave a visible handle, indicator line or permanent panel when hidden.
- Keep the activation strip small enough not to interfere with normal pointer use, but large enough to be reliable at common scale factors.
- Support a manual pin/lock-visible override for users who prefer a persistent bar.

## Hide behavior

- Start a short hide timer after the pointer leaves the bar and its interactive region.
- Cancel the timer while the pointer is over the bar, a menu is open, or the user is interacting with a control.
- Use a brief fade/slide transition; no spring or bounce animation.
- Respect reduced-motion settings by removing or minimizing the transition.
- Avoid rapid show/hide flicker when crossing the activation edge.
- Make the hide delay configurable. Begin testing around 500 ms, but do not treat that value as final until usability testing.

## Information hierarchy

The default bar should contain only these groups:

| Group | Initial contents | Rationale |
|---|---|---|
| Left | Workspace indicator | Show where the user is and allow quick workspace navigation |
| Center | Clock and date | Glanceable time without a permanent clock widget |
| Right | Battery (when present), network state, audio state, notification indicator | Essential laptop/system state and access to notification controls |

Rules:
- Do not add weather, music controls, CPU/RAM graphs, news, calendars, app launchers or decorative widgets to the default bar.
- Avoid duplicating information already obvious in the active application or overview.
- Hide hardware-specific indicators when the device does not support them.
- Prefer compact icons with accessible labels/tooltips; never rely on icon shape or color alone.
- Keep the notification indicator passive. Notifications themselves should not expand into a permanent feed on the bar.
- A system tray is not automatically required; add only the tray items needed for real compatibility and document their resource and interaction costs.

## Interaction

- Workspace items are clickable and keyboard accessible.
- Status items open small, focused controls only when activated.
- Menus close predictably with Escape and when focus moves away.
- Every interactive item has a visible focus state and accessible name.
- No essential operation may require hover alone.
- The bar must not steal focus from the active application just because it appears.
- Menus should not close when the pointer moves from the bar into the menu.

## Multi-monitor behavior

- Each monitor may reveal its own bar independently.
- The default should avoid showing duplicate controls on every monitor unless needed.
- Workspace state must reflect the monitor/workspace relationship exposed by Hyprland.
- Test top-edge gestures, mixed scale factors and monitor hotplug before considering the behavior stable.

## Runtime and performance

- Hidden means visually absent and idle: no continuous animation, high-frequency polling or needless redraw.
- Prefer compositor/system events for workspace, battery, network and audio updates.
- Avoid launching duplicate daemons for status information already provided by the system.
- Bound any caches and release menu-specific resources when menus close.
- The bar must not become a dependency for Hyprland window management.
- Keep a Waybar fallback available without requiring both bars to run simultaneously.

## Prototype acceptance checks

1. Pointer reveal works reliably at different scale factors.
2. Keyboard reveal works without colliding with the Super overview or existing Hyprland binds.
3. The bar does not flicker or disappear while interacting with menus.
4. It never steals focus from the active window on reveal.
5. It hides after the configured delay and remains fully idle while hidden.
6. Workspace, clock, battery, network, audio and notification states are accurate.
7. Missing hardware indicators disappear cleanly.
8. Reduced-motion mode works.
9. Multi-monitor and monitor hotplug behavior is predictable.
10. Idle CPU and memory are measured with the bar hidden and visible.

## Open questions

- Should the workspace indicator show numbers only, or a subtle active-window hint?
- Should the clock show date by default or reveal it on interaction?
- Which tray applications are essential for the initial Arch profile?
- Should pin-visible persist across sessions or only until the next logout?
- What keyboard shortcut feels natural without colliding with the overview?

Related: [Quiet defaults](QUIET-DEFAULTS.md), [Design principles](PRINCIPLES.md), [Keybindings](../KEYBINDINGS.md), [Performance](../PERFORMANCE.md).
