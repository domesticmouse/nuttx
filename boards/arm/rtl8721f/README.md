# `rtl8721f` Family Boards (`boards/arm/rtl8721f`)

## Overview
Intermediate blueprint grouping board support packages and shared board drivers for the `rtl8721f` SoC/MCU family under the `arm` architecture (1 subdirectories).

## Subdirectories & Boundaries
- [`rtl8721f_evb`](./rtl8721f_evb/README.md) - Board Support Package (BSP) blueprint for `rtl8721f_evb` (`arm` / `rtl8721f`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `adc`, `gpio`, `i2c`, `nsh`, `pwm`, `rtc` (+4 more).
