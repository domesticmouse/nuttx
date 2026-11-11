# `esp32c3-legacy-devkit` Board Support Package (`boards/risc-v/esp32c3-legacy/esp32c3-legacy-devkit`)

## Overview
Board Support Package (BSP) blueprint for `esp32c3-legacy-devkit` (`risc-v` / `esp32c3-legacy`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `adc`, `autopm`, `ble`, `bmp180`, `coremark`, `crypto` (+29 more).

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `esp32c3-legacy-devkit` (`risc-v/esp32c3-legacy`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 2 header file(s). Key symbols: `[board.h:BOARD_XTAL_FREQUENCY]` Hardware/board configuration macros (`BOARD_XTAL_FREQUENCY`, `BOARD_NGPIOOUT`, `BOARD_NGPIOINT`), `[board_memorymap.h:KIROM_START]` Hardware/board configuration macros (`KIROM_START`, `KIROM_SIZE`, `KDROM_START`, `KDROM_SIZE`, `KIRAM_START`, `KIRAM_SIZE` (+18 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `esp32c3-legacy-devkit` (`risc-v/esp32c3-legacy`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 7 source file(s). Key symbols: `[Make.defs:CSRCS]` Registered build sources in `Make.defs`, `[CMakeLists.txt:board]` CMake build target source registration.
