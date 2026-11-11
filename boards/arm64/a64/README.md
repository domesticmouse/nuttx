# `a64` Family Boards (`boards/arm64/a64`)

## Overview
Intermediate blueprint grouping board support packages and shared board drivers for the `a64` SoC/MCU family under the `arm64` architecture (1 subdirectories).

## Subdirectories & Boundaries
- [`pinephone`](./pinephone/README.md) - Board Support Package (BSP) blueprint for `pinephone` (`arm64` / `a64`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `lcd`, `lvgl`, `nsh`, `sensor`.
