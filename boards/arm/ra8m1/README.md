# `ra8m1` Family Boards (`boards/arm/ra8m1`)

## Overview
Intermediate blueprint grouping board support packages and shared board drivers for the `ra8m1` SoC/MCU family under the `arm` architecture (1 subdirectories).

## Subdirectories & Boundaries
- [`ek-ra8m1`](./ek-ra8m1/README.md) - Board Support Package (BSP) blueprint for `ek-ra8m1` (`arm` / `ra8m1`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`, `nsh-leds`, `serial-test`, `timer-gpio`.
