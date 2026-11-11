# `lpc214x` Family Boards (`boards/arm/lpc214x`)

## Overview
Intermediate blueprint grouping board support packages and shared board drivers for the `lpc214x` SoC/MCU family under the `arm` architecture (2 subdirectories).

## Subdirectories & Boundaries
- [`mcu123-lpc214x`](./mcu123-lpc214x/README.md) - Board Support Package (BSP) blueprint for `mcu123-lpc214x` (`arm` / `lpc214x`). Coordinates board initialization, headers, and tooling across `include, scripts, src`. Includes build configurations: `composite`, `nsh`, `usbmsc`, `usbserial`.
- [`zp214xpa`](./zp214xpa/README.md) - Board Support Package (BSP) blueprint for `zp214xpa` (`arm` / `lpc214x`). Coordinates board initialization, headers, and tooling across `include, src, tools`. Includes build configurations: `nsh`, `nxlines`.
