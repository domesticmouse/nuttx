# `flipnclick-sam3x/include` Component (`boards/arm/sam34/flipnclick-sam3x/include`)

## Overview
Board-level public headers (`include`) for `flipnclick-sam3x` (`arm/sam34`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:BOARD_32KOSC_FREQUENCY]` Hardware/board configuration macros (`BOARD_32KOSC_FREQUENCY`, `BOARD_SCLK_FREQUENCY`, `BOARD_MAINOSC_FREQUENCY`, `BOARD_CKGR_MOR_MOSCXTST`, `BOARD_CKGR_PLLAR_MUL`, `BOARD_CKGR_PLLAR_COUNT` (+32 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh flipnclick-sam3x:nsh && make`
