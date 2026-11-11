# `nrf91` Family Boards (`boards/arm/nrf91`)

## Overview
Intermediate blueprint grouping board support packages and shared board drivers for the `nrf91` SoC/MCU family under the `arm` architecture (3 subdirectories).

## Subdirectories & Boundaries
- [`common`](./common/README.md) - Board Support Package (BSP) blueprint for `common` (`arm` / `nrf91`). Coordinates board initialization, headers, and tooling across `include, src`.
- [`nrf9160-dk`](./nrf9160-dk/README.md) - Board Support Package (BSP) blueprint for `nrf9160-dk` (`arm` / `nrf91`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `mcuboot_app`, `mcuboot_loader`, `miniboot_s`, `modem_ns`, `nsh`, `ostest_tickless`.
- [`thingy91`](./thingy91/README.md) - Board Support Package (BSP) blueprint for `thingy91` (`arm` / `nrf91`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh_nrf52`, `nsh_rtt`, `thingy91_rtt`.
