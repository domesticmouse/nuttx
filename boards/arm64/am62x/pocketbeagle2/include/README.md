# `pocketbeagle2/include` Component (`boards/arm64/am62x/pocketbeagle2/include`)

## Overview
Board-level public headers (`include`) for `pocketbeagle2` (`arm64/am62x`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 2 header file(s).

## Interface
- `[board.h:BOARD_UART_SCLK]` Hardware/board configuration macros (`BOARD_UART_SCLK`, `BOARD_ARCH_TIMER_FREQ`, `BOARD_LED_USR0`, `BOARD_LED_USR1`, `BOARD_LED_USR2`, `BOARD_LED_USR3` (+16 more))
- `[board_memorymap.h:POCKETBEAGLE2_DEVICEIO_BASE]` Hardware/board configuration macros (`POCKETBEAGLE2_DEVICEIO_BASE`, `POCKETBEAGLE2_DEVICEIO_SIZE`, `POCKETBEAGLE2_DDR_BASE`, `POCKETBEAGLE2_DDR_SIZE`, `POCKETBEAGLE2_LOAD_ADDR`)

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh pocketbeagle2:nsh && make`
