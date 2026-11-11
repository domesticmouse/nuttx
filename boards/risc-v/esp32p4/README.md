# `esp32p4` Family Boards (`boards/risc-v/esp32p4`)

## Overview
Intermediate blueprint grouping board support packages and shared board drivers for the `esp32p4` SoC/MCU family under the `risc-v` architecture (4 subdirectories).

## Subdirectories & Boundaries
- [`common`](./common/README.md) - Board Support Package (BSP) blueprint for `common` (`risc-v` / `esp32p4`). Coordinates board initialization, headers, and tooling across `include, src`.
- [`esp32p4-function-ev-board`](./esp32p4-function-ev-board/README.md) - Board Support Package (BSP) blueprint for `esp32p4-function-ev-board` (`risc-v` / `esp32p4`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `adc`, `analog_cmpr`, `autopm`, `bmp180`, `buttons`, `capture` (+29 more).
- [`esp32p4-pico-wifi-wareshare`](./esp32p4-pico-wifi-wareshare/README.md) - Board Support Package (BSP) blueprint for `esp32p4-pico-wifi-wareshare` (`risc-v` / `esp32p4`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`, `spiflash`.
- [`esp32p4-tab5`](./esp32p4-tab5/README.md) - Board Support Package (BSP) blueprint for `esp32p4-tab5` (`risc-v` / `esp32p4`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `lvgl_demo`, `lvgl_term`, `nsh`, `python`, `sdmmc_spi`.
