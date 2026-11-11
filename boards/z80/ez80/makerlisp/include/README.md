# `makerlisp/include` Component (`boards/z80/ez80/makerlisp/include`)

## Overview
Board-level public headers (`include`) for `makerlisp` (`z80/ez80`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:EZ80_SYS_CLK_FREQ]` Hardware/board configuration macros (`EZ80_SYS_CLK_FREQ`, `LED_STARTED`, `LED_HEAPALLOCATE`, `LED_IRQSENABLED`, `LED_STACKCREATED`, `LED_IDLE` (+4 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh makerlisp:nsh_flash && make`
