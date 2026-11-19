# Design principles

Hyprcraft should feel polished and intentional while remaining fast, quiet and economical with system resources.

## Default experience

1. **Polish without clutter** — carefully considered typography, spacing, hierarchy and transitions; no ornamental UI for its own sake.
2. **Quiet by default** — the desktop stays out of the way while the user works.
3. **Essentials only** — persistent UI earns its place by providing useful, glanceable information.
4. **Space is a feature** — preserve screen area; avoid permanently visible panels and widgets without a clear purpose.
5. **Restraint** — color, blur, borders and motion are used only when they improve comprehension or feedback.
6. **Opt-in complexity** — extra widgets, dashboards, animations and integrations are optional and easy to disable.
7. **Keyboard power** — common tasks are fast and discoverable without a mouse.
8. **Memory is a design constraint** — avoid unnecessary resident processes, duplicate services, large caches and heavyweight effects.
9. **Performance is design** — avoid needless polling, background work and long-running animations.
10. **Accessible, not merely minimal** — minimalism must not hide controls, weaken contrast or make state unclear.
11. **Context-aware, not intrusive** — automatic behavior must be explainable, predictable and easy to override.

## Proposed interaction defaults

- The desktop bar uses **auto-hide** behavior rather than occupying screen space permanently.
- Focus mode is **automatic by default**, using explicit, user-configurable context rules rather than opaque guesses.
- Manual controls remain available: users can reveal the bar and override or pause automatic focus behavior.
- The Super-key full-screen overview remains the primary navigation surface.

These are proposed defaults for prototyping and community feedback, not immutable project decisions. See [Quiet defaults](QUIET-DEFAULTS.md).

## Feature test

Before adding a visible element or background service, ask:

- What user problem does it solve?
- Does it need to remain visible, or can it be summoned when needed?
- Can the user disable it independently?
- What attention, screen space, memory, CPU and startup cost does it add?
- Does it duplicate information or functionality already available elsewhere?
- Can it initialize only when needed and release resources afterward?

If the benefit is unclear, leave it out of the default profile.

## Community design process

These principles are a starting proposal, not one person's immutable taste. Discuss meaningful changes openly, explain trade-offs and record decisions so contributors can understand why a direction was chosen.

## Workflow

Observe a real problem, describe the user task, sketch the hierarchy, define the interaction, then implement. Do not begin by choosing a palette.
