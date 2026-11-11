# `nrf54l` Family Boards (`boards/arm/nrf54l`)

## Overview
Intermediate blueprint grouping board support packages and shared board drivers for the `nrf54l` SoC/MCU family under the `arm` architecture (2 subdirectories).

## Subdirectories & Boundaries
- [`nrf54l15-tag`](./nrf54l15-tag/README.md) - Board Support Package (BSP) blueprint for `nrf54l15-tag` (`arm` / `nrf54l`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`, `sdc`, `sensors`.
- [`nrf54lm20-dk`](./nrf54lm20-dk/README.md) - Board Support Package (BSP) blueprint for `nrf54lm20-dk` (`arm` / `nrf54l`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `ieee802154_6lowpan`, `ieee802154_mac`, `nsh`, `sdc`, `usbnsh`.
