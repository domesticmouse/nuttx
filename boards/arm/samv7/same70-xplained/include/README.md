# `same70-xplained/include` Component (`boards/arm/samv7/same70-xplained/include`)

## Overview
Board-level public headers (`include`) for `same70-xplained` (`arm/samv7`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:sam_lcdclear]` Public declaration `sam_lcdclear()`
- `[board.h:BOARD_SLOWCLK_FREQUENCY]` Hardware/board configuration macros (`BOARD_SLOWCLK_FREQUENCY`, `BOARD_MAINOSC_FREQUENCY`, `BOARD_CKGR_MOR_MOSCXTST`, `BOARD_CKGR_MOR_MOSCXTENBY`, `BOARD_CKGR_PLLAR_STMODE`, `BOARD_CKGR_PLLAR_COUNT` (+35 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh same70-xplained:nsh && make`
