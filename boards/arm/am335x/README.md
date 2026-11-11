# `am335x` Family Boards (`boards/arm/am335x`)

## Overview
Intermediate blueprint grouping board support packages and shared board drivers for the `am335x` SoC/MCU family under the `arm` architecture (2 subdirectories).

## Subdirectories & Boundaries
- [`beaglebone`](./beaglebone/README.md) - Board Support Package (BSP) blueprint for `beaglebone` (`arm` / `am335x`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `knsh`, `nsh`.
- [`beaglebone-black`](./beaglebone-black/README.md) - Board Support Package (BSP) blueprint for `beaglebone-black` (`arm` / `am335x`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `lcd`, `nsh`.
