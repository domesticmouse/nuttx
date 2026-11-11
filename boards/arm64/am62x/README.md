# `am62x` Family Boards (`boards/arm64/am62x`)

## Overview
Intermediate blueprint grouping board support packages and shared board drivers for the `am62x` SoC/MCU family under the `arm64` architecture (2 subdirectories).

## Subdirectories & Boundaries
- [`beagleplay`](./beagleplay/README.md) - Board Support Package (BSP) blueprint for `beagleplay` (`arm64` / `am62x`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `i2c`, `nsh`, `ostest`.
- [`pocketbeagle2`](./pocketbeagle2/README.md) - Board Support Package (BSP) blueprint for `pocketbeagle2` (`arm64` / `am62x`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `i2c`, `nsh`, `ostest`.
