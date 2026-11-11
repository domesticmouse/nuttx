# `rtl8721dx` Family Boards (`boards/arm/rtl8721dx`)

## Overview
Intermediate blueprint grouping board support packages and shared board drivers for the `rtl8721dx` SoC/MCU family under the `arm` architecture (1 subdirectories).

## Subdirectories & Boundaries
- [`pke8721daf`](./pke8721daf/README.md) - Board Support Package (BSP) blueprint for `pke8721daf` (`arm` / `rtl8721dx`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `adc`, `gpio`, `i2c`, `nsh`, `pwm`, `rtc` (+4 more).
