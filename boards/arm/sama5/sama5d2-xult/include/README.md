# `sama5d2-xult/include` Component (`boards/arm/sama5/sama5d2-xult/include`)

## Overview
Board-level public headers (`include`) for `sama5d2-xult` (`arm/sama5`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 7 header file(s).

## Interface
- `[board.h:BOARD_MAINOSC_FREQUENCY]` Hardware/board configuration macros (`BOARD_MAINOSC_FREQUENCY`, `BOARD_SLOWCLK_FREQUENCY`, `BOARD_UPLL_FREQUENCY`, `BOARD_LCDC_OUTPUT_BPP`, `BOARD_LCDC_WIDTH`, `BOARD_LCDC_HEIGHT` (+136 more))
- `[board_384mhz.h:BOARD_CKGR_MOR_MOSCXTST]` Hardware/board configuration macros (`BOARD_CKGR_MOR_MOSCXTST`, `BOARD_CKGR_PLLAR_COUNT`, `BOARD_CKGR_PLLAR_OUT`, `BOARD_CKGR_PLLAR_MUL`, `BOARD_PMC_MCKR_CSS`, `BOARD_PMC_MCKR_PRES` (+20 more))
- `[board_396mhz.h:BOARD_CKGR_MOR_MOSCXTST]` Hardware/board configuration macros (`BOARD_CKGR_MOR_MOSCXTST`, `BOARD_CKGR_PLLAR_COUNT`, `BOARD_CKGR_PLLAR_OUT`, `BOARD_CKGR_PLLAR_MUL`, `BOARD_PMC_MCKR_CSS`, `BOARD_PMC_MCKR_PRES` (+22 more))
- `[board_498mhz.h:BOARD_CKGR_MOR_MOSCXTST]` Hardware/board configuration macros (`BOARD_CKGR_MOR_MOSCXTST`, `BOARD_CKGR_PLLAR_COUNT`, `BOARD_CKGR_PLLAR_OUT`, `BOARD_CKGR_PLLAR_MUL`, `BOARD_PMC_MCKR_CSS`, `BOARD_PMC_MCKR_PRES` (+22 more))
- `[board_528mhz.h:BOARD_CKGR_MOR_MOSCXTST]` Hardware/board configuration macros (`BOARD_CKGR_MOR_MOSCXTST`, `BOARD_CKGR_PLLAR_COUNT`, `BOARD_CKGR_PLLAR_OUT`, `BOARD_CKGR_PLLAR_MUL`, `BOARD_PMC_MCKR_CSS`, `BOARD_PMC_MCKR_PRES` (+22 more))
- `[board_memorymap.h]` Board header declarations `board_memorymap.h`
- `[board_sdram.h:BOARD_MAINCK_FREQUENCY]` Hardware/board configuration macros (`BOARD_MAINCK_FREQUENCY`, `BOARD_PLLA_FREQUENCY`, `BOARD_PLLADIV2_FREQUENCY`, `BOARD_PCK_FREQUENCY`, `BOARD_MCK_FREQUENCY`, `BOARD_PIT_FREQUENCY` (+15 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh sama5d2-xult:nsh && make`
