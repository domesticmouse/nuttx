# `giant-board/include` Component (`boards/arm/sama5/giant-board/include`)

## Overview
Board-level public headers (`include`) for `giant-board` (`arm/sama5`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 4 header file(s).

## Interface
- `[board.h:BOARD_MAINOSC_FREQUENCY]` Hardware/board configuration macros (`BOARD_MAINOSC_FREQUENCY`, `BOARD_SLOWCLK_FREQUENCY`, `BOARD_ORANGE`, `BOARD_NLEDS`, `BOARD_ORANGE_BIT`, `LED_STARTED` (+20 more))
- `[board_492mhz.h:BOARD_CKGR_MOR_MOSCXTST]` Hardware/board configuration macros (`BOARD_CKGR_MOR_MOSCXTST`, `BOARD_CKGR_PLLAR_COUNT`, `BOARD_CKGR_PLLAR_OUT`, `BOARD_CKGR_PLLAR_MUL`, `BOARD_PMC_MCKR_CSS`, `BOARD_PMC_MCKR_PRES` (+22 more))
- `[board_memorymap.h]` Board header declarations `board_memorymap.h`
- `[board_sdram.h:BOARD_MAINCK_FREQUENCY]` Hardware/board configuration macros (`BOARD_MAINCK_FREQUENCY`, `BOARD_PLLA_FREQUENCY`, `BOARD_PLLADIV2_FREQUENCY`, `BOARD_PCK_FREQUENCY`, `BOARD_MCK_FREQUENCY`, `BOARD_PIT_FREQUENCY` (+15 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh giant-board:nsh && make`
