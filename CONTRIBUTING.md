# Contributing to Hyprcraft

Thanks for helping shape Hyprcraft. This is an early community project; you do not need to agree with every initial idea to contribute.

## Start with the problem

For a feature or significant change, open an issue first. Describe:

- The problem or workflow it improves
- Who benefits and in what situation
- Why existing tools or modules are insufficient
- Dependencies and resource costs
- Whether it belongs in the minimal default or an optional module

Small bug fixes, typo corrections and focused documentation improvements can go directly to a pull request.

## Branch workflow

Keep the repository to **10 branches maximum**, counting protected branches such as `main` and `dev`.

- Use `main` for stable releases and `dev` for integration.
- Prefer continuing work on an existing relevant feature branch rather than creating a new branch for every small follow-up.
- Use short-lived feature branches when work is independent and benefits from isolation.
- Before creating a branch, check the current branch count. Do not create one if it would exceed 10.
- Delete merged, abandoned or obsolete feature branches when they are no longer needed.
- Never delete `main` or `dev`; do not reuse either as a feature branch.
- Keep pull requests focused and target `dev` unless maintainers explicitly decide otherwise.

The branch limit is a repository hygiene rule, not a reason to combine unrelated changes into one branch.

## Design contributions

Hyprcraft aims for a quiet, minimal default desktop. Persistent UI should be rare and useful. Prefer on-demand interactions and optional modules over adding more always-visible elements.

A screenshot alone is not a design rationale. Explain hierarchy, behavior, keyboard access, scaling and the trade-offs.

## Code contributions

- Keep changes focused and modular.
- Preserve the separation between Hyprland core behavior and shell UI.
- Do not add required dependencies for optional features.
- Never include personal machine paths, credentials or device-specific configuration.
- Include validation steps and state clearly what you could not test.

## Discussion and decisions

Be constructive and open to alternatives. Significant changes should be discussed publicly and documented. The project is not intended to be dictated by one person's desktop preferences; community feedback should shape defaults and direction.

## Licensing

A project license has not yet been selected. Until one is added, do not assume that repository contents are available for unrestricted reuse or redistribution. Contributions and third-party assets must have clear provenance and compatible licensing before being merged.
