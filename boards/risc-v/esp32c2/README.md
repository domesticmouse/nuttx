# `esp32c2` Family Boards (`boards/risc-v/esp32c2`)

## Overview
Intermediate blueprint grouping board support packages and shared board drivers for the `esp32c2` SoC/MCU family under the `risc-v` architecture (2 subdirectories).

## Subdirectories & Boundaries
- [`common`](./common/README.md) - Board Support Package (BSP) blueprint for `common` (`risc-v` / `esp32c2`). Coordinates board initialization, headers, and tooling across `include, src`.
- [`esp8684-devkitm`](./esp8684-devkitm/README.md) - Board Support Package (BSP) blueprint for `esp8684-devkitm` (`risc-v` / `esp32c2`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `adc`, `ble`, `bmp180`, `buttons`, `crypto`, `efuse` (+17 more).
