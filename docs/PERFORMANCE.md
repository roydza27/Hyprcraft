# Performance and resource budget

> Status: requirements and measurement plan. Numeric budgets will be proposed only after a reproducible baseline is measured on documented hardware.

## Why this matters

Low memory usage is a first-class Hyprcraft requirement. The project should deliver a polished desktop without requiring a large always-running collection of services.

A visually refined interface is not permission to consume resources carelessly.

## Principles

- Keep the default process and dependency count small.
- Prefer native compositor capabilities and existing system services over duplicate daemons.
- Use event-driven updates instead of frequent polling.
- Lazy-load optional features and application browsing.
- Create window previews only when the overview is opened; release or reuse their buffers responsibly when it closes.
- Avoid continuous animations while idle.
- Bound image and application caches.
- Make optional modules disableable and ensure disabled modules do not start background work.
- Measure memory, CPU, startup time and interaction responsiveness together.

## Measurement scenarios

Record at least these scenarios:

1. **Compositor baseline:** Hyprland running without the Hyprcraft shell.
2. **Idle desktop:** default Hyprcraft session after startup settles.
3. **Overview open:** overview displayed with a representative number of windows.
4. **Search active:** application search filtering results.
5. **Optional feature:** one optional module enabled, measured separately.
6. **Shell restart:** confirm resources are released and do not accumulate after repeated restarts.

Record both per-process and total session memory. Distinguish RSS from PSS where tools support it; do not compare different memory metrics as if they were equivalent.

## Reproducibility

Every published result should include:

- CPU and RAM configuration
- GPU and driver where relevant
- Display resolution and scale factor
- Kernel, Hyprland, Quickshell and dependency versions
- Number and type of open windows
- Warm-up and measurement duration
- Exact commands or scripts used
- Memory metric reported (RSS, PSS, USS, etc.)
- Whether caches were warm or cold

Compare against the same machine and scenario. Avoid unsupported claims such as "uses only X MB" without reproducible evidence.

## Initial acceptance criteria

- The shell adds no avoidable resident services.
- The overview is not continuously rendering or polling while closed.
- Opening and closing the overview does not cause unbounded memory growth.
- Repeated shell restarts do not leak resources.
- Optional features are absent from the default startup path.
- Visual effects can be reduced or disabled on constrained hardware.

## Future numeric budgets

Once the first working implementation exists, gather measurements on more than one hardware class and agree on realistic targets through community discussion. Do not invent thresholds before there is a baseline.
