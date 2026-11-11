# `stm32u5` Family Boards (`boards/arm/stm32u5`)

## Overview
Intermediate blueprint grouping board support packages and shared board drivers for the `stm32u5` SoC/MCU family under the `arm` architecture (2 subdirectories).

## Subdirectories & Boundaries
- [`b-u585i-iot02a`](./b-u585i-iot02a/README.md) - Board Support Package (BSP) blueprint for `b-u585i-iot02a` (`arm` / `stm32u5`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`.
- [`nucleo-u5a5zj-q`](./nucleo-u5a5zj-q/README.md) - Board Support Package (BSP) blueprint for `nucleo-u5a5zj-q` (`arm` / `stm32u5`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`.
