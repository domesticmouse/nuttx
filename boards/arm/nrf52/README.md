# `nrf52` Family Boards (`boards/arm/nrf52`)

## Overview
Intermediate blueprint grouping board support packages and shared board drivers for the `nrf52` SoC/MCU family under the `arm` architecture (13 subdirectories).

## Subdirectories & Boundaries
- [`arduino-nano-33ble`](./arduino-nano-33ble/README.md) - Board Support Package (BSP) blueprint for `arduino-nano-33ble` (`arm` / `nrf52`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`, `usbnsh`.
- [`arduino-nano-33ble-rev2`](./arduino-nano-33ble-rev2/README.md) - Board Support Package (BSP) blueprint for `arduino-nano-33ble-rev2` (`arm` / `nrf52`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`, `usbnsh`.
- [`common`](./common/README.md) - Board Support Package (BSP) blueprint for `common` (`arm` / `nrf52`). Coordinates board initialization, headers, and tooling across `include, src`.
- [`nrf52-feather`](./nrf52-feather/README.md) - Board Support Package (BSP) blueprint for `nrf52-feather` (`arm` / `nrf52`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `i2c`, `nsh`, `userleds`.
- [`nrf52832-dk`](./nrf52832-dk/README.md) - Board Support Package (BSP) blueprint for `nrf52832-dk` (`arm` / `nrf52`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `jumbo`, `mcuboot_app`, `mcuboot_loader`, `mcuboot_loader_minimal`, `mrf24j40_6lowpan`, `mrf24j40_mac` (+6 more).
- [`nrf52832-mdk`](./nrf52832-mdk/README.md) - Board Support Package (BSP) blueprint for `nrf52832-mdk` (`arm` / `nrf52`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`.
- [`nrf52832-sparkfun`](./nrf52832-sparkfun/README.md) - Board Support Package (BSP) blueprint for `nrf52832-sparkfun` (`arm` / `nrf52`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`.
- [`nrf52840-dk`](./nrf52840-dk/README.md) - Board Support Package (BSP) blueprint for `nrf52840-dk` (`arm` / `nrf52`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `cdcacm`, `composite`, `highpri`, `ieee802154_6lowpan`, `ieee802154_mac`, `jumbo` (+8 more).
- [`nrf52840-dongle`](./nrf52840-dongle/README.md) - Board Support Package (BSP) blueprint for `nrf52840-dongle` (`arm` / `nrf52`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `ieee802154_mac`, `nsh`, `usbnsh`.
- [`nrf9160-dk-nrf52`](./nrf9160-dk-nrf52/README.md) - Board Support Package (BSP) blueprint for `nrf9160-dk-nrf52` (`arm` / `nrf52`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `ieee802154_6lowpan`, `ieee802154_mac`, `nsh`.
- [`thingy52`](./thingy52/README.md) - Board Support Package (BSP) blueprint for `thingy52` (`arm` / `nrf52`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`, `thingy_nimble`.
- [`thingy91-nrf52`](./thingy91-nrf52/README.md) - Board Support Package (BSP) blueprint for `thingy91-nrf52` (`arm` / `nrf52`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `usbnsh`.
- [`xiao-nrf52840`](./xiao-nrf52840/README.md) - Board Support Package (BSP) blueprint for `xiao-nrf52840` (`arm` / `nrf52`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `jumbo`, `nsh`, `usbnsh`.
