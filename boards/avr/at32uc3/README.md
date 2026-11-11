# `at32uc3` Family Boards (`boards/avr/at32uc3`)

## Overview
Intermediate blueprint grouping board support packages and shared board drivers for the `at32uc3` SoC/MCU family under the `avr` architecture (2 subdirectories).

## Subdirectories & Boundaries
- [`avr32dev1`](./avr32dev1/README.md) - Board Support Package (BSP) blueprint for `avr32dev1` (`avr` / `at32uc3`). Coordinates board initialization, headers, and tooling across `include, src, tools`. Includes build configurations: `nsh`, `ostest`.
- [`mizar32a`](./mizar32a/README.md) - Board Support Package (BSP) blueprint for `mizar32a` (`avr` / `at32uc3`). Coordinates board initialization, headers, and tooling across `include, src, tools`. Includes build configurations: `nsh`.
