# `stm32c5` Family Boards (`boards/arm/stm32c5`)

## Overview
Intermediate blueprint grouping board support packages and shared board drivers for the `stm32c5` SoC/MCU family under the `arm` architecture (1 subdirectories).

## Subdirectories & Boundaries
- [`nucleo-c562re`](./nucleo-c562re/README.md) - Board Support Package (BSP) blueprint for `nucleo-c562re` (`arm` / `stm32c5`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `jumbo`, `nsh`.
