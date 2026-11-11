# `sh1` Family Boards (`boards/renesas/sh1`)

## Overview
Intermediate blueprint grouping board support packages and shared board drivers for the `sh1` SoC/MCU family under the `renesas` architecture (1 subdirectories).

## Subdirectories & Boundaries
- [`us7032evb1`](./us7032evb1/README.md) - Board Support Package (BSP) blueprint for `us7032evb1` (`renesas` / `sh1`). Coordinates board initialization, headers, and tooling across `include, shterm, src`. Includes build configurations: `nsh`, `ostest`.
