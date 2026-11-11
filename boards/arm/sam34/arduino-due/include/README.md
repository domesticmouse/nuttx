# `arduino-due/include` Component (`boards/arm/sam34/arduino-due/include`)

## Overview
Board-level public headers (`include`) for `arduino-due` (`arm/sam34`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:BOARD_32KOSC_FREQUENCY]` Hardware/board configuration macros (`BOARD_32KOSC_FREQUENCY`, `BOARD_SCLK_FREQUENCY`, `BOARD_MAINOSC_FREQUENCY`, `BOARD_CKGR_MOR_MOSCXTST`, `BOARD_CKGR_PLLAR_MUL`, `BOARD_CKGR_PLLAR_COUNT` (+31 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh arduino-due:nsh && make`
