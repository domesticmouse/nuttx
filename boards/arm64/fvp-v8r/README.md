# `fvp-v8r` Family Boards (`boards/arm64/fvp-v8r`)

## Overview
Intermediate blueprint grouping board support packages and shared board drivers for the `fvp-v8r` SoC/MCU family under the `arm64` architecture (1 subdirectories).

## Subdirectories & Boundaries
- [`fvp-armv8r`](./fvp-armv8r/README.md) - Board Support Package (BSP) blueprint for `fvp-armv8r` (`arm64` / `fvp-v8r`). Coordinates board initialization, headers, and tooling across `include, kernel, src`. Includes build configurations: `citest`, `citest_smp`, `nsh`, `nsh_smp`, `pnsh`, `pnsh_smp`.
