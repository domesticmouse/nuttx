# `z80` Family Boards (`boards/z80/z80`)

## Overview
Intermediate blueprint grouping board support packages and shared board drivers for the `z80` SoC/MCU family under the `z80` architecture (1 subdirectories).

## Subdirectories & Boundaries
- [`z80sim`](./z80sim/README.md) - Board Support Package (BSP) blueprint for `z80sim` (`z80` / `z80`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`, `ostest`.
