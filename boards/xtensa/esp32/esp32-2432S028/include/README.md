# `esp32-2432S028/include` Component (`boards/xtensa/esp32/esp32-2432S028/include`)

## Overview
Board-level public headers (`include`) for `esp32-2432S028` (`xtensa/esp32`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 2 header file(s).

## Interface
- `[board.h:BOARD_XTAL_FREQUENCY]` Hardware/board configuration macros (`BOARD_XTAL_FREQUENCY`, `BOARD_CLOCK_FREQUENCY`, `DISPLAY_SPI`, `DISPLAY_DC`, `DISPLAY_RST`, `DISPLAY_BCKL` (+4 more))
- `[board_memorymap.h:KIROM_START]` Hardware/board configuration macros (`KIROM_START`, `KIROM_SIZE`, `KDROM_START`, `KDROM_SIZE`, `KIRAM_0_START`, `KIRAM_0_SIZE` (+24 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh esp32-2432S028:nsh && make`
