# `nrf53` Family Boards (`boards/arm/nrf53`)

## Overview
Intermediate blueprint grouping board support packages and shared board drivers for the `nrf53` SoC/MCU family under the `arm` architecture (4 subdirectories).

## Subdirectories & Boundaries
- [`common`](./common/README.md) - Board Support Package (BSP) blueprint for `common` (`arm` / `nrf53`). Coordinates board initialization, headers, and tooling across `include, src`.
- [`nrf5340-audio-dk`](./nrf5340-audio-dk/README.md) - Board Support Package (BSP) blueprint for `nrf5340-audio-dk` (`arm` / `nrf53`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh_cpuapp`.
- [`nrf5340-dk`](./nrf5340-dk/README.md) - Board Support Package (BSP) blueprint for `nrf5340-dk` (`arm` / `nrf53`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `adc_cpuapp`, `buttons_cpuapp`, `composite_cpuapp`, `ieee802154_6lowpan_cpunet`, `ieee802154_mac_cpunet`, `mcuboot_app_cpuapp` (+15 more).
- [`thingy53`](./thingy53/README.md) - Board Support Package (BSP) blueprint for `thingy53` (`arm` / `nrf53`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `composite_cpuapp`, `nsh_cpuapp`, `nsh_cpunet`, `rgbled_cpuapp`, `rpmsghci_nimble_cpuapp`, `rpmsghci_sdc_cpunet` (+2 more).
