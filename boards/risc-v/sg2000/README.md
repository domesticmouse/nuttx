# `sg2000` Family Boards (`boards/risc-v/sg2000`)

## Overview
Intermediate blueprint grouping board support packages and shared board drivers for the `sg2000` SoC/MCU family under the `risc-v` architecture (1 subdirectories).

## Subdirectories & Boundaries
- [`milkv_duos`](./milkv_duos/README.md) - Board Support Package (BSP) blueprint for `milkv_duos` (`risc-v` / `sg2000`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`.
