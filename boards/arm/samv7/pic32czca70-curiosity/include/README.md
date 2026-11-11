# `pic32czca70-curiosity/include` Component (`boards/arm/samv7/pic32czca70-curiosity/include`)

## Overview
Board-level public headers (`include`) for `pic32czca70-curiosity` (`arm/samv7`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:BOARD_HAVE_SLOWXTAL]` Hardware/board configuration macros (`BOARD_HAVE_SLOWXTAL`, `BOARD_SLOWCLK_FREQUENCY`, `BOARD_MAINOSC_FREQUENCY`, `BOARD_CKGR_MOR_MOSCXTST`, `BOARD_CKGR_MOR_MOSCXTENBY`, `BOARD_CKGR_PLLAR_STMODE` (+34 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh pic32czca70-curiosity:nsh && make`
