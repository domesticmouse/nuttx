# `fvp-armv8r/include` Component (`boards/arm64/fvp-v8r/fvp-armv8r/include`)

## Overview
Board-level public headers (`include`) for `fvp-armv8r` (`arm64/fvp-v8r`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 2 header file(s).

## Interface
- `[board.h]` Board header declarations `board.h`
- `[board_memorymap.h:KTEXT_SIZE]` Hardware/board configuration macros (`KTEXT_SIZE`, `KSRAM_SIZE`, `UTEXT_SIZE`, `USRAM_SIZE`, `KTEXT_START`, `KTEXT_END` (+6 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh fvp-armv8r:nsh && make`
