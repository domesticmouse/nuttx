# `stm32f7` Family Boards (`boards/arm/stm32f7`)

## Overview
Intermediate blueprint grouping board support packages and shared board drivers for the `stm32f7` SoC/MCU family under the `arm` architecture (8 subdirectories).

## Subdirectories & Boundaries
- [`nucleo-f722ze`](./nucleo-f722ze/README.md) - Board Support Package (BSP) blueprint for `nucleo-f722ze` (`arm` / `stm32f7`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `can`, `cansock`, `composite`, `nsh`.
- [`nucleo-f746zg`](./nucleo-f746zg/README.md) - Board Support Package (BSP) blueprint for `nucleo-f746zg` (`arm` / `stm32f7`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `evalos`, `lorawan_gw`, `note`, `nsh`, `pysim`.
- [`nucleo-f767zi`](./nucleo-f767zi/README.md) - Board Support Package (BSP) blueprint for `nucleo-f767zi` (`arm` / `stm32f7`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `evalos`, `netnsh`, `nsh`.
- [`steval-eth001v1`](./steval-eth001v1/README.md) - Board Support Package (BSP) blueprint for `steval-eth001v1` (`arm` / `stm32f7`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `foc_b16`, `foc_f32`, `nsh`.
- [`stm32f746-ws`](./stm32f746-ws/README.md) - Board Support Package (BSP) blueprint for `stm32f746-ws` (`arm` / `stm32f7`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`.
- [`stm32f746g-disco`](./stm32f746g-disco/README.md) - Board Support Package (BSP) blueprint for `stm32f746g-disco` (`arm` / `stm32f7`). Coordinates board initialization, headers, and tooling across `include, kernel, src`. Includes build configurations: `audio`, `dropbear`, `fb`, `lvgl`, `netnsh`, `nsh` (+2 more).
- [`stm32f769i-disco`](./stm32f769i-disco/README.md) - Board Support Package (BSP) blueprint for `stm32f769i-disco` (`arm` / `stm32f7`). Coordinates board initialization, headers, and tooling across `include, kernel, src`. Includes build configurations: `netnsh`, `nsh`.
- [`stm32f777zit6-meadow`](./stm32f777zit6-meadow/README.md) - Board Support Package (BSP) blueprint for `stm32f777zit6-meadow` (`arm` / `stm32f7`). Coordinates board initialization, headers, and tooling across `include, kernel, src`. Includes build configurations: `dualcdcacm`, `f7corecomp`, `i2s`, `meadow_os`, `nsh`, `projectlab` (+2 more).
