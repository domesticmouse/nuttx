# `stm32f0` Family Boards (`boards/arm/stm32f0`)

## Overview
Intermediate blueprint grouping board support packages and shared board drivers for the `stm32f0` SoC/MCU family under the `arm` architecture (4 subdirectories).

## Subdirectories & Boundaries
- [`nucleo-f072rb`](./nucleo-f072rb/README.md) - Board Support Package (BSP) blueprint for `nucleo-f072rb` (`arm` / `stm32f0`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`, `usb-cdc-uart`.
- [`nucleo-f091rc`](./nucleo-f091rc/README.md) - Board Support Package (BSP) blueprint for `nucleo-f091rc` (`arm` / `stm32f0`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`, `sx127x`.
- [`stm32f051-discovery`](./stm32f051-discovery/README.md) - Board Support Package (BSP) blueprint for `stm32f051-discovery` (`arm` / `stm32f0`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`.
- [`stm32f072-discovery`](./stm32f072-discovery/README.md) - Board Support Package (BSP) blueprint for `stm32f072-discovery` (`arm` / `stm32f0`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`.
