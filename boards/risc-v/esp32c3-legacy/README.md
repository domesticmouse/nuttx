# `esp32c3-legacy` Family Boards (`boards/risc-v/esp32c3-legacy`)

## Overview
Intermediate blueprint grouping board support packages and shared board drivers for the `esp32c3-legacy` SoC/MCU family under the `risc-v` architecture (3 subdirectories).

## Subdirectories & Boundaries
- [`common`](./common/README.md) - Board Support Package (BSP) blueprint for `common` (`risc-v` / `esp32c3-legacy`). Coordinates board initialization, headers, and tooling across `include, kernel, src`.
- [`esp32c3-legacy-devkit`](./esp32c3-legacy-devkit/README.md) - Board Support Package (BSP) blueprint for `esp32c3-legacy-devkit` (`risc-v` / `esp32c3-legacy`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `adc`, `autopm`, `ble`, `bmp180`, `coremark`, `crypto` (+29 more).
- [`esp32c3-legacy-devkit-rust-1`](./esp32c3-legacy-devkit-rust-1/README.md) - Board Support Package (BSP) blueprint for `esp32c3-legacy-devkit-rust-1` (`risc-v` / `esp32c3-legacy`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `brickmatch`, `nsh`.
