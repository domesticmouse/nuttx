# `sam3u-ek/include` Component (`boards/arm/sam34/sam3u-ek/include`)

## Overview
Board-level public headers (`include`) for `sam3u-ek` (`arm/sam34`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:BOARD_CKGR_MOR_MOSCXTST]` Hardware/board configuration macros (`BOARD_CKGR_MOR_MOSCXTST`, `BOARD_CKGR_PLLAR_MUL`, `BOARD_CKGR_PLLAR_STMODE`, `BOARD_CKGR_PLLAR_COUNT`, `BOARD_CKGR_PLLAR_DIV`, `BOARD_PMC_MCKR_CSS` (+21 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh sam3u-ek:nsh && make`
