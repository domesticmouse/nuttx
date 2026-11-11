# `bl602` Family Boards (`boards/risc-v/bl602`)

## Overview
Intermediate blueprint grouping board support packages and shared board drivers for the `bl602` SoC/MCU family under the `risc-v` architecture (1 subdirectories).

## Subdirectories & Boundaries
- [`bl602evb`](./bl602evb/README.md) - Board Support Package (BSP) blueprint for `bl602evb` (`risc-v` / `bl602`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `dma`, `elf`, `fpu`, `gpio`, `i2c`, `nsh` (+4 more).
