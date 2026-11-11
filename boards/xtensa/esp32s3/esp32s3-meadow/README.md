# `esp32s3-meadow` Board Support Package (`boards/xtensa/esp32s3/esp32s3-meadow`)

## Overview
Board Support Package (BSP) blueprint for `esp32s3-meadow` (`xtensa` / `esp32s3`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`, `usbnsh`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `esp32s3-meadow` (`xtensa/esp32s3`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 2 header file(s). Key symbols: `[board.h:BOARD_XTAL_FREQUENCY]` Hardware/board configuration macros (`BOARD_XTAL_FREQUENCY`, `BOARD_CLOCK_FREQUENCY`, `BOARD_NLEDS`), `[board_memorymap.h:KIROM_START]` Hardware/board configuration macros (`KIROM_START`, `KIROM_SIZE`, `KDROM_START`, `KDROM_SIZE`, `KIRAM_START`, `KIRAM_SIZE` (+18 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `esp32s3-meadow` (`xtensa/esp32s3`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 4 source file(s). Key symbols: `[Make.defs:CSRCS]` Registered build sources in `Make.defs`, `[esp32s3-meadow.h:esp32s3_bringup]` Public declaration `esp32s3_bringup()`.
