# `misoc/include` Component (`boards/misoc/lm32/misoc/include`)

## Overview
Board-level public headers (`include`) for `misoc` (`misoc/lm32`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:BOARD_XTAL_FREQ]` Hardware/board configuration macros (`BOARD_XTAL_FREQ`, `BOARD_CPU_CLOCK`, `BOARD_TOSCK_CLOCK`, `LED_STARTED`, `LED_HEAPALLOCATE`, `LED_IRQSENABLED` (+5 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh misoc:nsh && make`
