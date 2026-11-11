# `stm32l4` Family Boards (`boards/arm/stm32l4`)

## Overview
Intermediate blueprint grouping board support packages and shared board drivers for the `stm32l4` SoC/MCU family under the `arm` architecture (9 subdirectories).

## Subdirectories & Boundaries
- [`b-l475e-iot01a`](./b-l475e-iot01a/README.md) - Board Support Package (BSP) blueprint for `b-l475e-iot01a` (`arm` / `stm32l4`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`, `qemu`, `spirit-6lowpan`, `spirit-starhub`, `spirit-starpoint`.
- [`nucleo-l432kc`](./nucleo-l432kc/README.md) - Board Support Package (BSP) blueprint for `nucleo-l432kc` (`arm` / `stm32l4`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`, `spwm`, `wgen`.
- [`nucleo-l452re`](./nucleo-l452re/README.md) - Board Support Package (BSP) blueprint for `nucleo-l452re` (`arm` / `stm32l4`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`.
- [`nucleo-l476rg`](./nucleo-l476rg/README.md) - Board Support Package (BSP) blueprint for `nucleo-l476rg` (`arm` / `stm32l4`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`, `nxdemo`.
- [`nucleo-l496zg`](./nucleo-l496zg/README.md) - Board Support Package (BSP) blueprint for `nucleo-l496zg` (`arm` / `stm32l4`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`.
- [`steval-stlcs01v1`](./steval-stlcs01v1/README.md) - Board Support Package (BSP) blueprint for `steval-stlcs01v1` (`arm` / `stm32l4`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `lwl`, `usbnsh`.
- [`stm32l476-mdk`](./stm32l476-mdk/README.md) - Board Support Package (BSP) blueprint for `stm32l476-mdk` (`arm` / `stm32l4`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`.
- [`stm32l476vg-disco`](./stm32l476vg-disco/README.md) - Board Support Package (BSP) blueprint for `stm32l476vg-disco` (`arm` / `stm32l4`). Coordinates board initialization, headers, and tooling across `include, kernel, src`. Includes build configurations: `knsh`, `nsh`.
- [`stm32l4r9ai-disco`](./stm32l4r9ai-disco/README.md) - Board Support Package (BSP) blueprint for `stm32l4r9ai-disco` (`arm` / `stm32l4`). Coordinates board initialization, headers, and tooling across `include, kernel, src`. Includes build configurations: `knsh`, `nsh`.
