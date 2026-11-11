# `rtl8730e` Family Boards (`boards/arm/rtl8730e`)

## Overview
Intermediate blueprint grouping board support packages and shared board drivers for the `rtl8730e` SoC/MCU family under the `arm` architecture (1 subdirectories).

## Subdirectories & Boundaries
- [`rtl8730e_evb`](./rtl8730e_evb/README.md) - Board Support Package (BSP) blueprint for `rtl8730e_evb` (`arm` / `rtl8730e`). Coordinates board initialization, headers, and tooling across `include, prebuilt, src`. Includes build configurations: `adc`, `gpio`, `i2c`, `nsh`, `pwm`, `rtc` (+4 more).
