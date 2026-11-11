# `esp32c6` Family Boards (`boards/risc-v/esp32c6`)

## Overview
Intermediate blueprint grouping board support packages and shared board drivers for the `esp32c6` SoC/MCU family under the `risc-v` architecture (4 subdirectories).

## Subdirectories & Boundaries
- [`common`](./common/README.md) - Board Support Package (BSP) blueprint for `common` (`risc-v` / `esp32c6`). Coordinates board initialization, headers, and tooling across `include, src`.
- [`esp32c6-devkitc`](./esp32c6-devkitc/README.md) - Board Support Package (BSP) blueprint for `esp32c6-devkitc` (`risc-v` / `esp32c6`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `adc`, `autopm`, `ble`, `bmp180`, `buttons`, `capture` (+34 more).
- [`esp32c6-devkitm`](./esp32c6-devkitm/README.md) - Board Support Package (BSP) blueprint for `esp32c6-devkitm` (`risc-v` / `esp32c6`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `bmp180`, `buttons`, `efuse`, `gpio`, `i2c`, `i2schar` (+20 more).
- [`esp32c6-xiao`](./esp32c6-xiao/README.md) - Board Support Package (BSP) blueprint for `esp32c6-xiao` (`risc-v` / `esp32c6`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `gpio`, `nsh`, `usbnsh`, `wifi`.
