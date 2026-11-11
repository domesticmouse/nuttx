# `ea3152/include` Component (`boards/arm/lpc31xx/ea3152/include`)

## Overview
Board-level public headers (`include`) for `ea3152` (`arm/lpc31xx`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 2 header file(s).

## Interface
- `[board.h:BOARD_FREQIN_FFAST]` Hardware/board configuration macros (`BOARD_FREQIN_FFAST`, `BOARD_HPLL0_FINSEL`, `BOARD_HPLL0_NDEC`, `BOARD_HPLL0_MDEC`, `BOARD_HPLL0_PDEC`, `BOARD_HPLL0_SELR` (+24 more))
- `[board_memorymap.h:LPC31_SHADOWSPACE_VSECTION]` Hardware/board configuration macros (`LPC31_SHADOWSPACE_VSECTION`, `LPC31_INTSRAM_VSECTION`, `LPC31_INTSRAM0_VADDR`, `LPC31_INTSRAM1_VADDR`, `LPC31_INTSROM0_VSECTION`, `LPC31_APB01_VSECTION` (+18 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh ea3152:ostest && make`
