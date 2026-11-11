# `moxa/include` Component (`boards/arm/moxart/moxa/include`)

## Overview
Board-level public headers (`include`) for `moxa` (`arm/moxart`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:ftintc010_set_trig_mode]` Public declaration `ftintc010_set_trig_mode()`
- `[board.h:ftintc010_set_trig_level]` Public declaration `ftintc010_set_trig_level()`
- `[board.h:BOARD_32KOSC_FREQUENCY]` Hardware/board configuration macros (`BOARD_32KOSC_FREQUENCY`, `BOARD_SCLK_FREQUENCY`, `BOARD_MAINOSC_FREQUENCY`, `BOARD_CKGR_MOR_MOSCXTST`, `BOARD_CKGR_PLLAR_MUL`, `BOARD_CKGR_PLLAR_COUNT` (+27 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh moxa:nsh && make`
