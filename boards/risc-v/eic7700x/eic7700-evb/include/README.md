# `eic7700-evb/include` Component (`boards/risc-v/eic7700x/eic7700-evb/include`)

## Overview
Board-level public headers (`include`) for `eic7700-evb` (`risc-v/eic7700x`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 2 header file(s).

## Interface
- `[board.h:eic7700x_boardinitialize]` Public declaration `eic7700x_boardinitialize()`
- `[board_memorymap.h:KFLASH_START]` Hardware/board configuration macros (`KFLASH_START`, `KFLASH_SIZE`, `KSRAM_START`, `KSRAM_SIZE`, `KSRAM_END`, `PGPOOL_START` (+4 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh eic7700-evb:nsh && make`
