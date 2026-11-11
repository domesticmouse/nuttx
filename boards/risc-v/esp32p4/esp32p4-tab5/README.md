# `esp32p4-tab5` Board Support Package (`boards/risc-v/esp32p4/esp32p4-tab5`)

## Overview
Board Support Package (BSP) blueprint for `esp32p4-tab5` (`risc-v` / `esp32p4`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `lvgl_demo`, `lvgl_term`, `nsh`, `python`, `sdmmc_spi`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `esp32p4-tab5` (`risc-v/esp32p4`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:TAB5_GPIO_PC_TX]` Hardware/board configuration macros (`TAB5_GPIO_PC_TX`, `TAB5_GPIO_PC_RX`, `TAB5_GPIO_I2C0_SDA`, `TAB5_GPIO_I2C0_SCL`, `TAB5_GPIO_GROVE_SDA`, `TAB5_GPIO_GROVE_SCL` (+57 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `esp32p4-tab5` (`risc-v/esp32p4`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 18 source file(s). Key symbols: `[Make.defs:CSRCS]` Registered build sources in `Make.defs`, `[CMakeLists.txt:board]` CMake build target source registration.
