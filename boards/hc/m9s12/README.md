# `m9s12` Family Boards (`boards/hc/m9s12`)

## Overview
Intermediate blueprint grouping board support packages and shared board drivers for the `m9s12` SoC/MCU family under the `hc` architecture (2 subdirectories).

## Subdirectories & Boundaries
- [`demo9s12ne64`](./demo9s12ne64/README.md) - Board Support Package (BSP) blueprint for `demo9s12ne64` (`hc` / `m9s12`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `ostest`.
- [`ne64badge`](./ne64badge/README.md) - Board Support Package (BSP) blueprint for `ne64badge` (`hc` / `m9s12`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `ostest`.
