# `sam4cmp-db/include` Component (`boards/arm/sam34/sam4cmp-db/include`)

## Overview
Board-level public headers (`include`) for `sam4cmp-db` (`arm/sam34`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:BOARD_CKGR_MOR_MOSCXTST]` Hardware/board configuration macros (`BOARD_CKGR_MOR_MOSCXTST`, `BOARD_MAINOSC_FREQUENCY`, `BOARD_CKGR_PLLAR_MUL`, `BOARD_CKGR_PLLAR_DIV`, `BOARD_CKGR_PLLAR_COUNT`, `BOARD_PLLA_FREQUENCY` (+11 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh sam4cmp-db:nsh && make`
