# `olimex-lpc-h3131/include` Component (`boards/arm/lpc31xx/olimex-lpc-h3131/include`)

## Overview
Board-level public headers (`include`) for `olimex-lpc-h3131` (`arm/lpc31xx`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 2 header file(s).

## Interface
- `[board.h:lpc31_setup_overcurrent]` Public declaration `lpc31_setup_overcurrent()`
- `[board.h:BOARD_FREQIN_FFAST]` Hardware/board configuration macros (`BOARD_FREQIN_FFAST`, `BOARD_HPLL0_FINSEL`, `BOARD_HPLL0_NDEC`, `BOARD_HPLL0_MDEC`, `BOARD_HPLL0_PDEC`, `BOARD_HPLL0_SELR` (+29 more))
- `[board_memorymap.h:LPC31_SHADOWSPACE_VSECTION]` Hardware/board configuration macros (`LPC31_SHADOWSPACE_VSECTION`, `LPC31_INTSRAM_VSECTION`, `LPC31_INTSRAM0_VADDR`, `LPC31_INTSRAM1_VADDR`, `LPC31_INTSROM0_VSECTION`, `LPC31_APB01_VSECTION` (+18 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh olimex-lpc-h3131:nsh && make`
