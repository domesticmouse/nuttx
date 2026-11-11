# `eic7700x` Family Boards (`boards/risc-v/eic7700x`)

## Overview
Intermediate blueprint grouping board support packages and shared board drivers for the `eic7700x` SoC/MCU family under the `risc-v` architecture (3 subdirectories).

## Subdirectories & Boundaries
- [`common`](./common/README.md) - Board Support Package (BSP) blueprint for `common` (`risc-v` / `eic7700x`). Coordinates board initialization, headers, and tooling across `src, tools`.
- [`eic7700-evb`](./eic7700-evb/README.md) - Board Support Package (BSP) blueprint for `eic7700-evb` (`risc-v` / `eic7700x`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`.
- [`starpro64`](./starpro64/README.md) - Board Support Package (BSP) blueprint for `starpro64` (`risc-v` / `eic7700x`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`.
