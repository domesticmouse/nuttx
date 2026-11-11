# `stm32l0` Family Boards (`boards/arm/stm32l0`)

## Overview
Intermediate blueprint grouping board support packages and shared board drivers for the `stm32l0` SoC/MCU family under the `arm` architecture (3 subdirectories).

## Subdirectories & Boundaries
- [`b-l072z-lrwan1`](./b-l072z-lrwan1/README.md) - Board Support Package (BSP) blueprint for `b-l072z-lrwan1` (`arm` / `stm32l0`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `adc`, `lorawan_beacon`, `lorawan_tx`, `nsh`, `nxlines_oled`, `sx127x`.
- [`nucleo-l073rz`](./nucleo-l073rz/README.md) - Board Support Package (BSP) blueprint for `nucleo-l073rz` (`arm` / `stm32l0`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`, `sx127x`, `usb-cdc`.
- [`stm32l0538-disco`](./stm32l0538-disco/README.md) - Board Support Package (BSP) blueprint for `stm32l0538-disco` (`arm` / `stm32l0`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`.
