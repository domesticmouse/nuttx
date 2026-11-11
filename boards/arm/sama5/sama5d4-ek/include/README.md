# `sama5d4-ek/include` Component (`boards/arm/sama5/sama5d4-ek/include`)

## Overview
Board-level public headers (`include`) for `sama5d4-ek` (`arm/sama5`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 6 header file(s).

## Interface
- `[board.h:BOARD_MAINOSC_FREQUENCY]` Hardware/board configuration macros (`BOARD_MAINOSC_FREQUENCY`, `BOARD_SLOWCLK_FREQUENCY`, `BOARD_USER`, `BOARD_POWER`, `BOARD_NLEDS`, `BOARD_USER_BIT` (+37 more))
- `[board_384mhz.h:BOARD_CKGR_MOR_MOSCXTST]` Hardware/board configuration macros (`BOARD_CKGR_MOR_MOSCXTST`, `BOARD_CKGR_PLLAR_COUNT`, `BOARD_CKGR_PLLAR_OUT`, `BOARD_CKGR_PLLAR_MUL`, `BOARD_PMC_MCKR_CSS`, `BOARD_PMC_MCKR_PRES` (+19 more))
- `[board_396mhz.h:BOARD_CKGR_MOR_MOSCXTST]` Hardware/board configuration macros (`BOARD_CKGR_MOR_MOSCXTST`, `BOARD_CKGR_PLLAR_COUNT`, `BOARD_CKGR_PLLAR_OUT`, `BOARD_CKGR_PLLAR_MUL`, `BOARD_PMC_MCKR_CSS`, `BOARD_PMC_MCKR_PRES` (+21 more))
- `[board_528mhz.h:BOARD_CKGR_MOR_MOSCXTST]` Hardware/board configuration macros (`BOARD_CKGR_MOR_MOSCXTST`, `BOARD_CKGR_PLLAR_COUNT`, `BOARD_CKGR_PLLAR_OUT`, `BOARD_CKGR_PLLAR_MUL`, `BOARD_PMC_MCKR_CSS`, `BOARD_PMC_MCKR_PRES` (+21 more))
- `[board_memorymap.h]` Board header declarations `board_memorymap.h`
- `[board_sdram.h:BOARD_MAINCK_FREQUENCY]` Hardware/board configuration macros (`BOARD_MAINCK_FREQUENCY`, `BOARD_PLLA_FREQUENCY`, `BOARD_PLLADIV2_FREQUENCY`, `BOARD_PCK_FREQUENCY`, `BOARD_MCK_FREQUENCY`, `BOARD_PIT_FREQUENCY` (+14 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh sama5d4-ek:nsh && make`
