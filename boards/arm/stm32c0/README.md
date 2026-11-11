# `stm32c0` Family Boards (`boards/arm/stm32c0`)

## Overview
Intermediate blueprint grouping board support packages and shared board drivers for the `stm32c0` SoC/MCU family under the `arm` architecture (2 subdirectories).

## Subdirectories & Boundaries
- [`nucleo-c071rb`](./nucleo-c071rb/README.md) - Board Support Package (BSP) blueprint for `nucleo-c071rb` (`arm` / `stm32c0`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `adcscope`, `jumbo`, `nsh`, `usb-cdc`.
- [`nucleo-c092rc`](./nucleo-c092rc/README.md) - Board Support Package (BSP) blueprint for `nucleo-c092rc` (`arm` / `stm32c0`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `can`, `cansock`, `jumbo`, `nsh`.
