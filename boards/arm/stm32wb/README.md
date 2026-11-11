# `stm32wb` Family Boards (`boards/arm/stm32wb`)

## Overview
Intermediate blueprint grouping board support packages and shared board drivers for the `stm32wb` SoC/MCU family under the `arm` architecture (2 subdirectories).

## Subdirectories & Boundaries
- [`flipperzero`](./flipperzero/README.md) - Board Support Package (BSP) blueprint for `flipperzero` (`arm` / `stm32wb`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`.
- [`nucleo-wb55rg`](./nucleo-wb55rg/README.md) - Board Support Package (BSP) blueprint for `nucleo-wb55rg` (`arm` / `stm32wb`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `ble`, `nimble`, `nsh`.
