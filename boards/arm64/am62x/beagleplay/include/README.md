# `beagleplay/include` Component (`boards/arm64/am62x/beagleplay/include`)

## Overview
Board-level public headers (`include`) for `beagleplay` (`arm64/am62x`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 2 header file(s).

## Interface
- `[board.h:BOARD_UART_SCLK]` Hardware/board configuration macros (`BOARD_UART_SCLK`, `BOARD_ARCH_TIMER_FREQ`, `BOARD_LED_USR0`, `BOARD_LED_USR1`, `BOARD_LED_USR2`, `BOARD_LED_USR3` (+13 more))
- `[board_memorymap.h:BEAGLEPLAY_DEVICEIO_BASE]` Hardware/board configuration macros (`BEAGLEPLAY_DEVICEIO_BASE`, `BEAGLEPLAY_DEVICEIO_SIZE`, `BEAGLEPLAY_DDR_BASE`, `BEAGLEPLAY_DDR_SIZE`, `BEAGLEPLAY_LOAD_ADDR`)

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh beagleplay:nsh && make`
