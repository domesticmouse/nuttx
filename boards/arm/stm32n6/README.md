# `stm32n6` Family Boards (`boards/arm/stm32n6`)

## Overview
Intermediate blueprint grouping board support packages and shared board drivers for the `stm32n6` SoC/MCU family under the `arm` architecture (2 subdirectories).

## Subdirectories & Boundaries
- [`nucleo-n657x0-q`](./nucleo-n657x0-q/README.md) - Board Support Package (BSP) blueprint for `nucleo-n657x0-q` (`arm` / `stm32n6`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `leds`, `nsh`, `ostest`.
- [`stm32n6570-dk`](./stm32n6570-dk/README.md) - Board Support Package (BSP) blueprint for `stm32n6570-dk` (`arm` / `stm32n6`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`.
