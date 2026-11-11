# `esp32c3` Family Boards (`boards/risc-v/esp32c3`)

## Overview
Intermediate blueprint grouping board support packages and shared board drivers for the `esp32c3` SoC/MCU family under the `risc-v` architecture (5 subdirectories).

## Subdirectories & Boundaries
- [`common`](./common/README.md) - Board Support Package (BSP) blueprint for `common` (`risc-v` / `esp32c3`). Coordinates board initialization, headers, and tooling across `include, src`.
- [`esp32-c3-zero`](./esp32-c3-zero/README.md) - Board Support Package (BSP) blueprint for `esp32-c3-zero` (`risc-v` / `esp32c3`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `jumbo`, `nsh`, `sta_softap`, `usbnsh`, `wifi`.
- [`esp32c3-devkit`](./esp32c3-devkit/README.md) - Board Support Package (BSP) blueprint for `esp32c3-devkit` (`risc-v` / `esp32c3`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `adc`, `autopm`, `ble`, `bmp180`, `buttons`, `crypto` (+29 more).
- [`esp32c3-supermini`](./esp32c3-supermini/README.md) - Board Support Package (BSP) blueprint for `esp32c3-supermini` (`risc-v` / `esp32c3`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `gpio`, `nsh`, `usbnsh`, `wifi`.
- [`esp32c3-xiao`](./esp32c3-xiao/README.md) - Board Support Package (BSP) blueprint for `esp32c3-xiao` (`risc-v` / `esp32c3`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `ble`, `gpio`, `nimble`, `nsh`, `smartfs`, `usbnsh` (+1 more).
