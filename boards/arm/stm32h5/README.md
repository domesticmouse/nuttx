# `stm32h5` Family Boards (`boards/arm/stm32h5`)

## Overview
Intermediate blueprint grouping board support packages and shared board drivers for the `stm32h5` SoC/MCU family under the `arm` architecture (4 subdirectories).

## Subdirectories & Boundaries
- [`nucleo-h503rb`](./nucleo-h503rb/README.md) - Board Support Package (BSP) blueprint for `nucleo-h503rb` (`arm` / `stm32h5`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`.
- [`nucleo-h533re`](./nucleo-h533re/README.md) - Board Support Package (BSP) blueprint for `nucleo-h533re` (`arm` / `stm32h5`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`.
- [`nucleo-h563zi`](./nucleo-h563zi/README.md) - Board Support Package (BSP) blueprint for `nucleo-h563zi` (`arm` / `stm32h5`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `adc`, `adc_watchdog`, `buttons`, `capture`, `dac`, `dts` (+7 more).
- [`stm32h573i-dk`](./stm32h573i-dk/README.md) - Board Support Package (BSP) blueprint for `stm32h573i-dk` (`arm` / `stm32h5`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `jumbo`, `nsh`.
