# `lpc31xx` Family Boards (`boards/arm/lpc31xx`)

## Overview
Intermediate blueprint grouping board support packages and shared board drivers for the `lpc31xx` SoC/MCU family under the `arm` architecture (3 subdirectories).

## Subdirectories & Boundaries
- [`ea3131`](./ea3131/README.md) - Board Support Package (BSP) blueprint for `ea3131` (`arm` / `lpc31xx`). Coordinates board initialization, headers, and tooling across `include, locked, src, tools`. Includes build configurations: `nsh`, `pgnsh`, `usbserial`.
- [`ea3152`](./ea3152/README.md) - Board Support Package (BSP) blueprint for `ea3152` (`arm` / `lpc31xx`). Coordinates board initialization, headers, and tooling across `include, src, tools`. Includes build configurations: `ostest`.
- [`olimex-lpc-h3131`](./olimex-lpc-h3131/README.md) - Board Support Package (BSP) blueprint for `olimex-lpc-h3131` (`arm` / `lpc31xx`). Coordinates board initialization, headers, and tooling across `include, src, tools`. Includes build configurations: `nsh`.
