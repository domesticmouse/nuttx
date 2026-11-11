# `litex` Family Boards (`boards/risc-v/litex`)

## Overview
Intermediate blueprint grouping board support packages and shared board drivers for the `litex` SoC/MCU family under the `risc-v` architecture (1 subdirectories).

## Subdirectories & Boundaries
- [`arty_a7`](./arty_a7/README.md) - Board Support Package (BSP) blueprint for `arty_a7` (`risc-v` / `litex`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `knsh`, `knsh-tickless`, `netnsh`, `nsh`, `nsh-tickless`, `nsh-vexii` (+2 more).
