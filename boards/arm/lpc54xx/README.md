# `lpc54xx` Family Boards (`boards/arm/lpc54xx`)

## Overview
Intermediate blueprint grouping board support packages and shared board drivers for the `lpc54xx` SoC/MCU family under the `arm` architecture (1 subdirectories).

## Subdirectories & Boundaries
- [`lpcxpresso-lpc54628`](./lpcxpresso-lpc54628/README.md) - Board Support Package (BSP) blueprint for `lpcxpresso-lpc54628` (`arm` / `lpc54xx`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `fb`, `lvgl`, `netnsh`, `nsh`, `nxwm`, `pwfb` (+3 more).
