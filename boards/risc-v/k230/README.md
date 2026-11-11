# `k230` Family Boards (`boards/risc-v/k230`)

## Overview
Intermediate blueprint grouping board support packages and shared board drivers for the `k230` SoC/MCU family under the `risc-v` architecture (1 subdirectories).

## Subdirectories & Boundaries
- [`canmv230`](./canmv230/README.md) - Board Support Package (BSP) blueprint for `canmv230` (`risc-v` / `k230`). Coordinates board initialization, headers, and tooling across `include, kernel, src`. Includes build configurations: `knsh`, `master`, `nsbi`, `nsh`, `pnsh`, `remote`.
