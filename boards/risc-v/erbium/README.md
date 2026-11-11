# `erbium` Family Boards (`boards/risc-v/erbium`)

## Overview
Intermediate blueprint grouping board support packages and shared board drivers for the `erbium` SoC/MCU family under the `risc-v` architecture (1 subdirectories).

## Subdirectories & Boundaries
- [`minion`](./minion/README.md) - Board Support Package (BSP) blueprint for `minion` (`risc-v` / `erbium`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`, `ostest`.
