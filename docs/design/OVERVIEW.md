# Desktop overview

> Status: interaction proposal. This is a design specification, not an implemented or finalized interface. Community feedback is welcome.

## Purpose

The overview is Hyprcraft's central navigation surface. It gives users a spatial summary of their open windows and workspaces, while providing a direct path to application search and launch.

It is opened with the Super key. It should feel like a natural extension of the desktop rather than a separate application.

The design takes inspiration from the clarity and polish of macOS and the workspace-oriented overview in GNOME, while retaining Hyprland's keyboard-first window-management model. It must establish its own layout, behavior and visual identity.

## Design goals

- Make the current desktop state understandable at a glance.
- Make switching windows and workspaces fast with keyboard or pointer.
- Make application search available without opening a second launcher.
- Keep the normal desktop free of persistent overview UI.
- Use restrained transitions and minimal visual decoration.
- Remain responsive and usable across monitor sizes and scale factors.
- Keep window management in Hyprland; Quickshell presents and navigates the overview.

## Proposed information hierarchy

1. **Search** — a prominent, immediately available field for applications and optionally open windows.
2. **Workspaces** — a compact visual strip of workspaces, with the active workspace clearly identified.
3. **Window overview** — previews of windows on the selected workspace, with readable titles and app identity.
4. **Application access** — a way to browse applications when search is empty or the user chooses app browsing.

The overview should not show system dashboards, large widgets, news, weather or unrelated content.

## Entry and exit

| Input | Proposed behavior |
|---|---|
| Super | Toggle the overview |
| Escape | Close the overview and return to the prior desktop state |
| Click outside | Close only when it does not cause an accidental action |
| Select a window | Close overview and focus that window |
| Select a workspace | Switch to that workspace; keep overview open for continued navigation |
| Search and Enter | Launch the best matching application or select the highlighted result |

The Super binding must not conflict with the normal Hyprland modifier workflows. The implementation should use a reliable press/release or compositor-supported toggle strategy and must be tested for key-repeat and held-key edge cases.

## Keyboard interaction

The overview is fully navigable without a pointer.

| Input | Proposed behavior |
|---|---|
| Type printable characters | Focus search and begin filtering |
| Up / Down | Move through search results or window cards |
| Left / Right | Move between workspace items or cards |
| Enter | Activate the selected result |
| Escape | Clear search first; if empty, close overview |
| Tab / Shift+Tab | Move between major overview regions |
| Super + number | Preserve direct workspace switching outside the overview; inside, may select the corresponding workspace if implemented consistently |

Do not capture established Hyprland window-management shortcuts unnecessarily. The exact key map is to be validated in a running session and documented in the keybinding reference.

## Pointer interaction

- Clicking a window preview focuses that window.
- Clicking a workspace selects it.
- Dragging a window preview to another workspace may move the window there; this must have clear visual feedback and a safe drop target.
- Clicking an application result launches it.
- Avoid hover-only controls; essential actions must be discoverable and keyboard accessible.

Drag-and-drop is a later enhancement, not a requirement for the first implementation.

## Search behavior

Search should be integrated into the overview rather than opening a visually unrelated launcher.

Initial scope:
- Search installed applications by name.
- Show a clear empty state and no-results state.
- Support keyboard selection and launch.
- Keep matching fast and avoid unnecessary background polling.

Potential later scope:
- Search open windows.
- Search actions or settings.
- Calculator or command providers.

Additional providers must be modular and opt-in. Do not turn the default search into a noisy universal search product.

## Visual and motion direction

- Use a calm backdrop treatment that separates the overview from the desktop without obscuring context completely.
- Use consistent window preview proportions and clear app identity.
- Use typography and spacing to establish hierarchy; avoid ornamental borders and excessive shadows.
- Keep workspace selection obvious without relying on color alone.
- Use short, purposeful transitions. Respect reduced-motion preferences.
- Avoid parallax, spring-heavy motion, exaggerated zooms and continuous animation.
- Do not require blur; provide a good fallback when blur is unavailable or expensive.

## State model

The first implementation should distinguish these states:

- `closed`: overview is not visible.
- `overview`: overview visible, no search query.
- `searching`: query entered and results visible.
- `browsing-apps`: application browsing view is active.
- `no-results`: search has no matches.

State transitions must be predictable. Escape clears a non-empty query before closing. Activating a window or app closes the overview after the action is accepted.

## Component responsibilities

**Hyprland**
- Owns windows, workspaces, focus and moving windows.
- Exposes the compositor state needed by the shell.
- Retains all essential keyboard window-management behavior.

**Quickshell**
- Renders the overview and window previews.
- Provides search UI and application results.
- Handles overview navigation and presentation state.
- Requests focus or workspace changes through supported Hyprland interfaces.

The overview must not become the owner of window state or a dependency for normal desktop operation.

## Accessibility and performance

- Keyboard navigation must cover every primary action.
- Focus must be visible.
- Text and selection states must meet readable contrast.
- Support reduced motion and different scale factors.
- Avoid polling compositor state when event-driven updates are available.
- Avoid keeping expensive previews or animations active while the overview is closed.
- Degrade gracefully if preview capture is unavailable.

## Delivery stages

### Stage 1 — Functional overview
- Super toggles overview.
- Display current workspace and its windows.
- Select a window to focus it.
- Switch workspaces.
- Escape closes the overview.
- Keyboard navigation works.

### Stage 2 — Integrated application search
- Search installed applications.
- Navigate results and launch.
- Clear and no-results states.

### Stage 3 — Refinement
- Improve previews and transitions.
- Add app browsing.
- Validate multi-monitor behavior and scaling.
- Consider optional drag-and-drop.

## Open design questions

These are intentionally open for community discussion:

- Should workspace thumbnails be a horizontal strip or a side rail?
- Should the overview show windows from the active workspace only, or all workspaces?
- Should application browsing be a separate mode or an expandable section?
- How should multiple monitors be represented?
- Which parts of the overview should be configurable without fragmenting the default experience?

Do not treat the proposed layout or interaction details as settled until they have been tested and discussed.
