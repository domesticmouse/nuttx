# `stm32u0` Family Boards (`boards/arm/stm32u0`)

## Overview
Intermediate blueprint grouping board support packages and shared board drivers for the `stm32u0` SoC/MCU family under the `arm` architecture (2 subdirectories).

## Subdirectories & Boundaries
- [`nucleo-u083rc`](./nucleo-u083rc/README.md) - Board Support Package (BSP) blueprint for `nucleo-u083rc` (`arm` / `stm32u0`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `jumbo`, `nsh`.
- [`stm32u083c-dk`](./stm32u083c-dk/README.md) - Board Support Package (BSP) blueprint for `stm32u083c-dk` (`arm` / `stm32u0`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `jumbo`, `nsh`.
