# `stm32l5` Family Boards (`boards/arm/stm32l5`)

## Overview
Intermediate blueprint grouping board support packages and shared board drivers for the `stm32l5` SoC/MCU family under the `arm` architecture (2 subdirectories).

## Subdirectories & Boundaries
- [`nucleo-l552ze`](./nucleo-l552ze/README.md) - Board Support Package (BSP) blueprint for `nucleo-l552ze` (`arm` / `stm32l5`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`.
- [`stm32l562e-dk`](./stm32l562e-dk/README.md) - Board Support Package (BSP) blueprint for `stm32l562e-dk` (`arm` / `stm32l5`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`.
