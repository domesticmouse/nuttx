# `sam4l-xplained/include` Component (`boards/arm/sam34/sam4l-xplained/include`)

## Overview
Board-level public headers (`include`) for `sam4l-xplained` (`arm/sam34`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:BOARD_SYSCLK_SOURCE_DFLL0]` Hardware/board configuration macros (`BOARD_SYSCLK_SOURCE_DFLL0`, `BOARD_RCSYS_FREQUENCY`, `BOARD_RC32K_FREQUENCY`, `BOARD_RC80M_FREQUENCY`, `BOARD_RCFAST4M_FREQUENCY`, `BOARD_RCFAST8M_FREQUENCY` (+46 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh sam4l-xplained:nsh && make`
