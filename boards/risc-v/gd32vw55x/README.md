# `gd32vw55x` Family Boards (`boards/risc-v/gd32vw55x`)

## Overview
Intermediate blueprint grouping board support packages and shared board drivers for the `gd32vw55x` SoC/MCU family under the `risc-v` architecture (2 subdirectories).

## Subdirectories & Boundaries
- [`gd32vw553-hmq`](./gd32vw553-hmq/README.md) - Board Support Package (BSP) blueprint for `gd32vw553-hmq` (`risc-v` / `gd32vw55x`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `ble`, `nsh`, `ostest`, `sta_softap`, `wapi`.
- [`gd32vw553k-start`](./gd32vw553k-start/README.md) - Board Support Package (BSP) blueprint for `gd32vw553k-start` (`risc-v` / `gd32vw55x`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `adc`, `ble`, `littlefs`, `nsh`, `ostest`, `periph` (+6 more).
