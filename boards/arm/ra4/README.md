# `ra4` Family Boards (`boards/arm/ra4`)

## Overview
Intermediate blueprint grouping board support packages and shared board drivers for the `ra4` SoC/MCU family under the `arm` architecture (2 subdirectories).

## Subdirectories & Boundaries
- [`arduino-r4-minima`](./arduino-r4-minima/README.md) - Board Support Package (BSP) blueprint for `arduino-r4-minima` (`arm` / `ra4`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`, `nsh-leds`, `pwm`.
- [`xiao-ra4m1`](./xiao-ra4m1/README.md) - Board Support Package (BSP) blueprint for `xiao-ra4m1` (`arm` / `ra4`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `combo`, `nsh`.
