# Design tokens

This file defines the token contract, not a color palette. Values will be selected after the first visual direction is explored and tested.

## Token groups

- `color.surface.*`: desktop, panel, card and overlay surfaces.
- `color.text.*`: primary, secondary, muted and inverse text.
- `color.accent.*`: interactive emphasis and selected states.
- `color.status.*`: success, warning, error and informational states.
- `space.*`: consistent spacing scale.
- `radius.*`: corner radius scale.
- `type.*`: font family, size, weight and line-height roles.
- `motion.*`: duration and easing roles.
- `layer.*`: overlay and surface stacking order.

## Rules

- Prefer semantic names over component-specific names.
- Components consume tokens; they should not invent their own global palette.
- Keep contrast and readability ahead of decorative effects.
- Document theme-specific values separately from token meanings.
