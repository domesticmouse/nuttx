# `stm32f2` Family Boards (`boards/arm/stm32f2`)

## Overview
Intermediate blueprint grouping board support packages and shared board drivers for the `stm32f2` SoC/MCU family under the `arm` architecture (5 subdirectories).

## Subdirectories & Boundaries
- [`emw3162`](./emw3162/README.md) - Board Support Package (BSP) blueprint for `emw3162` (`arm` / `stm32f2`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`, `wlan`.
- [`nucleo-f207zg`](./nucleo-f207zg/README.md) - Board Support Package (BSP) blueprint for `nucleo-f207zg` (`arm` / `stm32f2`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `adc`, `nsh`, `pwm`.
- [`olimex-stm32-p207`](./olimex-stm32-p207/README.md) - Board Support Package (BSP) blueprint for `olimex-stm32-p207` (`arm` / `stm32f2`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`.
- [`photon`](./photon/README.md) - Board Support Package (BSP) blueprint for `photon` (`arm` / `stm32f2`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `adb`, `nsh`, `rgbled`, `usbnsh`, `wlan`, `wlan-perf`.
- [`stm3220g-eval`](./stm3220g-eval/README.md) - Board Support Package (BSP) blueprint for `stm3220g-eval` (`arm` / `stm32f2`). Coordinates board initialization, headers, and tooling across `include, src, tools`. Includes build configurations: `dhcpd`, `nettest`, `nsh`, `nsh2`, `nxwm`, `telnetd`.
