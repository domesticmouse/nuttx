# `bl808` Family Boards (`boards/risc-v/bl808`)

## Overview
Intermediate blueprint grouping board support packages and shared board drivers for the `bl808` SoC/MCU family under the `risc-v` architecture (1 subdirectories).

## Subdirectories & Boundaries
- [`ox64`](./ox64/README.md) - Board Support Package (BSP) blueprint for `ox64` (`risc-v` / `bl808`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `adc`, `nsh`, `spi`, `timer`.
