# `c906` Family Boards (`boards/risc-v/c906`)

## Overview
Intermediate blueprint grouping board support packages and shared board drivers for the `c906` SoC/MCU family under the `risc-v` architecture (1 subdirectories).

## Subdirectories & Boundaries
- [`smartl-c906`](./smartl-c906/README.md) - Board Support Package (BSP) blueprint for `smartl-c906` (`risc-v` / `c906`). Coordinates board initialization, headers, and tooling across `include, kernel, src`. Includes build configurations: `elf`, `fpu`, `knsh`, `module`, `nsh`, `sotest`.
