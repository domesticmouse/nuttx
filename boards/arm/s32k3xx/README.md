# `s32k3xx` Family Boards (`boards/arm/s32k3xx`)

## Overview
Intermediate blueprint grouping board support packages and shared board drivers for the `s32k3xx` SoC/MCU family under the `arm` architecture (2 subdirectories).

## Subdirectories & Boundaries
- [`mr-canhubk3`](./mr-canhubk3/README.md) - Board Support Package (BSP) blueprint for `mr-canhubk3` (`arm` / `s32k3xx`). Coordinates board initialization, headers, and tooling across `include, kernel, src`. Includes build configurations: `knsh`, `net`, `nsh`.
- [`s32k344evb`](./s32k344evb/README.md) - Board Support Package (BSP) blueprint for `s32k344evb` (`arm` / `s32k3xx`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`.
