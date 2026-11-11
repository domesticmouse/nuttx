# `pinephone/include` Component (`boards/arm64/a64/pinephone/include`)

## Overview
Board-level public headers (`include`) for `pinephone` (`arm64/a64`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 2 header file(s).

## Interface
- `[board.h:BOARD_LED1_BIT]` Hardware/board configuration macros (`BOARD_LED1_BIT`, `BOARD_LED2_BIT`, `BOARD_LED3_BIT`, `LED_STARTED`, `LED_HEAPALLOCATE`, `LED_IRQSENABLED` (+6 more))
- `[board_memorymap.h]` Board header declarations `board_memorymap.h`

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh pinephone:nsh && make`
