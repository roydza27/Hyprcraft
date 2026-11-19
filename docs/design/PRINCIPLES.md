# Design principles

Hyprcraft should be a calm workspace, not another thing competing for the user's attention.

## Default experience

1. **Quiet by default** — the desktop stays out of the way while the user works.
2. **Essentials only** — persistent UI earns its place by providing useful, glanceable information.
3. **Space is a feature** — preserve screen area; avoid permanently visible panels and widgets without a clear purpose.
4. **Hierarchy before decoration** — important information is immediately legible.
5. **Restraint** — color, blur, borders and motion are used only when they improve comprehension or feedback.
6. **Opt-in complexity** — extra widgets, dashboards, animations and integrations are optional and easy to disable.
7. **Keyboard parity** — common tasks are efficient without a mouse.
8. **Performance is design** — avoid needless polling, background services and heavyweight effects.
9. **Accessible, not merely minimal** — minimalism must not hide controls, weaken contrast or make state unclear.

## Feature test

Before adding a visible element, ask:

- What user problem does it solve?
- Does it need to remain visible, or can it be summoned when needed?
- Can the user disable it independently?
- What attention, screen space, memory and CPU does it cost?
- Does it duplicate information already available elsewhere?

If the benefit is unclear, leave it out of the default profile.

## Community design process

These principles are a starting proposal, not one person's immutable taste. Discuss meaningful changes openly, explain trade-offs and record decisions so contributors can understand why a direction was chosen.

## Workflow

Observe a real problem, describe the user task, sketch the hierarchy, define the interaction, then implement. Do not begin by choosing a palette.
