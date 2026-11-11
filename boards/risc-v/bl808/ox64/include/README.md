# `ox64/include` Component (`boards/risc-v/bl808/ox64/include`)

## Overview
Board-level public headers (`include`) for `ox64` (`risc-v/bl808`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 2 header file(s).

## Interface
- `[board.h:bl808_boardinitialize]` Public declaration `bl808_boardinitialize()`
- `[board.h:BOARD_LED1_BIT]` Hardware/board configuration macros (`BOARD_LED1_BIT`, `BOARD_LED2_BIT`, `BOARD_LED3_BIT`, `LED_STARTED`, `LED_HEAPALLOCATE`, `LED_IRQSENABLED` (+6 more))
- `[board_memorymap.h:BL808_DDR_BASE]` Hardware/board configuration macros (`BL808_DDR_BASE`, `BL808_DDR_SIZE`, `KFLASH_START`, `KFLASH_SIZE`, `KSRAM_START`, `KSRAM_SIZE` (+6 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh ox64:nsh && make`
