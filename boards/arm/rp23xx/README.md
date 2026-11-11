# `rp23xx` Family Boards (`boards/arm/rp23xx`)

## Overview
Intermediate blueprint grouping board support packages and shared board drivers for the `rp23xx` SoC/MCU family under the `arm` architecture (6 subdirectories).

## Subdirectories & Boundaries
- [`common`](./common/README.md) - Board Support Package (BSP) blueprint for `common` (`arm` / `rp23xx`). Coordinates board initialization, headers, and tooling across `include, src`.
- [`pimoroni-pico-2-plus`](./pimoroni-pico-2-plus/README.md) - Board Support Package (BSP) blueprint for `pimoroni-pico-2-plus` (`arm` / `rp23xx`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `audiopack`, `composite`, `nsh`, `nshsram`, `pm`, `smp` (+6 more).
- [`pimoroni-pico-plus-2-w`](./pimoroni-pico-plus-2-w/README.md) - Board Support Package (BSP) blueprint for `pimoroni-pico-plus-2-w` (`arm` / `rp23xx`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`, `usbnsh`, `wifi`.
- [`raspberrypi-pico-2`](./raspberrypi-pico-2/README.md) - Board Support Package (BSP) blueprint for `raspberrypi-pico-2` (`arm` / `rp23xx`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`, `pm`, `smp`, `spisd`, `usbnsh`, `userled`.
- [`raspberrypi-pico-2-w`](./raspberrypi-pico-2-w/README.md) - Board Support Package (BSP) blueprint for `raspberrypi-pico-2-w` (`arm` / `rp23xx`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `composite`, `telnet`.
- [`xiao-rp2350`](./xiao-rp2350/README.md) - Board Support Package (BSP) blueprint for `xiao-rp2350` (`arm` / `rp23xx`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `combo`, `nsh`, `usbnsh`.
