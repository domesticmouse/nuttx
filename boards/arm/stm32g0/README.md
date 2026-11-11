# `stm32g0` Family Boards (`boards/arm/stm32g0`)

## Overview
Intermediate blueprint grouping board support packages and shared board drivers for the `stm32g0` SoC/MCU family under the `arm` architecture (5 subdirectories).

## Subdirectories & Boundaries
- [`nucleo-g070rb`](./nucleo-g070rb/README.md) - Board Support Package (BSP) blueprint for `nucleo-g070rb` (`arm` / `stm32g0`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`.
- [`nucleo-g071rb`](./nucleo-g071rb/README.md) - Board Support Package (BSP) blueprint for `nucleo-g071rb` (`arm` / `stm32g0`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`.
- [`nucleo-g0b1re`](./nucleo-g0b1re/README.md) - Board Support Package (BSP) blueprint for `nucleo-g0b1re` (`arm` / `stm32g0`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `adc`, `adc_dma`, `nsh`, `usb-cdc`, `usb-clocks`.
- [`stm32g071b-disco`](./stm32g071b-disco/README.md) - Board Support Package (BSP) blueprint for `stm32g071b-disco` (`arm` / `stm32g0`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`, `oled`.
- [`weact-stm32g0b1`](./weact-stm32g0b1/README.md) - Board Support Package (BSP) blueprint for `weact-stm32g0b1` (`arm` / `stm32g0`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `buttons`, `dronecan`, `nsh`, `userled`.
