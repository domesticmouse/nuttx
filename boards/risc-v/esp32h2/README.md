# `esp32h2` Family Boards (`boards/risc-v/esp32h2`)

## Overview
Intermediate blueprint grouping board support packages and shared board drivers for the `esp32h2` SoC/MCU family under the `risc-v` architecture (2 subdirectories).

## Subdirectories & Boundaries
- [`common`](./common/README.md) - Board Support Package (BSP) blueprint for `common` (`risc-v` / `esp32h2`). Coordinates board initialization, headers, and tooling across `include, src`.
- [`esp32h2-devkit`](./esp32h2-devkit/README.md) - Board Support Package (BSP) blueprint for `esp32h2-devkit` (`risc-v` / `esp32h2`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `adc`, `analog_cmpr`, `autopm`, `ble`, `bmp180`, `buttons` (+27 more).
