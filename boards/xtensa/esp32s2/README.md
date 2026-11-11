# `esp32s2` Family Boards (`boards/xtensa/esp32s2`)

## Overview
Intermediate blueprint grouping board support packages and shared board drivers for the `esp32s2` SoC/MCU family under the `xtensa` architecture (4 subdirectories).

## Subdirectories & Boundaries
- [`common`](./common/README.md) - Board Support Package (BSP) blueprint for `common` (`xtensa` / `esp32s2`). Coordinates board initialization, headers, and tooling across `include, src`.
- [`esp32s2-kaluga-1`](./esp32s2-kaluga-1/README.md) - Board Support Package (BSP) blueprint for `esp32s2-kaluga-1` (`xtensa` / `esp32s2`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `audio`, `buttons`, `i2c`, `lvgl_ili9341`, `lvgl_st7789`, `nsh` (+4 more).
- [`esp32s2-saola-1`](./esp32s2-saola-1/README.md) - Board Support Package (BSP) blueprint for `esp32s2-saola-1` (`xtensa` / `esp32s2`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `adc`, `audio`, `buttons`, `coremark`, `crypto`, `cxx` (+29 more).
- [`franzininho-wifi`](./franzininho-wifi/README.md) - Board Support Package (BSP) blueprint for `franzininho-wifi` (`xtensa` / `esp32s2`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`.
