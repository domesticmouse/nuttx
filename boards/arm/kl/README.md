# `kl` Family Boards (`boards/arm/kl`)

## Overview
Intermediate blueprint grouping board support packages and shared board drivers for the `kl` SoC/MCU family under the `arm` architecture (3 subdirectories).

## Subdirectories & Boundaries
- [`freedom-kl25z`](./freedom-kl25z/README.md) - Board Support Package (BSP) blueprint for `freedom-kl25z` (`arm` / `kl`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`.
- [`freedom-kl26z`](./freedom-kl26z/README.md) - Board Support Package (BSP) blueprint for `freedom-kl26z` (`arm` / `kl`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`.
- [`teensy-lc`](./teensy-lc/README.md) - Board Support Package (BSP) blueprint for `teensy-lc` (`arm` / `kl`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`.
