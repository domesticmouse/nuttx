# `stm32l1` Family Boards (`boards/arm/stm32l1`)

## Overview
Intermediate blueprint grouping board support packages and shared board drivers for the `stm32l1` SoC/MCU family under the `arm` architecture (2 subdirectories).

## Subdirectories & Boundaries
- [`nucleo-l152re`](./nucleo-l152re/README.md) - Board Support Package (BSP) blueprint for `nucleo-l152re` (`arm` / `stm32l1`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `lcd`, `nsh`.
- [`stm32ldiscovery`](./stm32ldiscovery/README.md) - Board Support Package (BSP) blueprint for `stm32ldiscovery` (`arm` / `stm32l1`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `chrono`, `nsh`.
