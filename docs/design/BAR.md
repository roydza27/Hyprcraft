# Minimal desktop bar

> Status: selected visual direction for prototyping. Proposed for community feedback; not implemented or finalized.

## Purpose

The bar is a temporary status surface, not a dashboard. It should make a small set of useful facts available at a glance, then leave the screen to the user's work.

**Selected direction:** a full-width, top-edge bar that auto-hides.

The bar should read as one calm, continuous strip attached to the monitor edge—not a floating island, a collection of cards, or a widget dashboard. Its visual polish should come from alignment, typography, spacing and restrained materials rather than decoration.

## Visual structure

Use one full-width horizontal surface divided into three predictable zones:

| Zone | Contents | Alignment |
|---|---|---|
| Left | Workspace indicator | Start |
| Center | Clock and date | True horizontal center |
| Right | Battery (when present), network, audio and notification indicator | End |

Layout requirements:
- The bar spans the available width of its monitor.
- Left and right groups must not push the clock away from the true center; use a layout that centers independently of the side-group widths.
- Keep the bar visually thin and compact. Exact height, padding and typography are tokenized and will be selected through a running prototype.
- Use consistent icon size, baseline alignment and spacing.
- Avoid separate rounded cards or pill backgrounds around each status item.
- Use a subtle surface distinction from the desktop. Prefer a simple surface with restrained opacity; blur is optional and must never be required.
- Avoid heavy shadows, thick borders, gradients, decorative separators and excessive corner rounding.
- Use a subtle divider or tonal change only when it improves grouping.
- Keep labels readable. Icons may be paired with short text where state would otherwise be ambiguous.

## Placement and reveal

- Place the bar along the top edge of each configured monitor.
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
- The bar is a status/navigation surface, not an application launcher; launching apps belongs in the Super overview.

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
- Blur and transparency must have a low-cost fallback and must not increase the baseline dependency set.

## Prototype acceptance checks

1. The bar reads as one continuous full-width strip, not three floating panels.
2. The clock remains geometrically centered with unequal left/right content.
3. Pointer reveal works reliably at different scale factors.
4. Keyboard reveal works without colliding with the Super overview or existing Hyprland binds.
5. The bar does not flicker or disappear while interacting with menus.
6. It never steals focus from the active window on reveal.
7. It hides after the configured delay and remains fully idle while hidden.
8. Workspace, clock, battery, network, audio and notification states are accurate.
9. Missing hardware indicators disappear cleanly.
10. Reduced-motion mode works.
11. Multi-monitor and monitor hotplug behavior is predictable.
12. Idle CPU and memory are measured with the bar hidden and visible, with blur disabled and enabled.

## Open questions

- Should the workspace indicator show numbers only, or a subtle active-window hint?
- Should the clock show date by default or reveal it on interaction?
- Which tray applications are essential for the initial Arch profile?
- Should pin-visible persist across sessions or only until the next logout?
- What keyboard shortcut feels natural without colliding with the overview?
- What surface opacity and bar height remain readable without making the bar visually heavy?

Related: [Quiet defaults](QUIET-DEFAULTS.md), [Design principles](PRINCIPLES.md), [Keybindings](../KEYBINDINGS.md), [Performance](../PERFORMANCE.md).
