# `us7032evb1/include` Component (`boards/renesas/sh1/us7032evb1/include`)

## Overview
Board-level public headers (`include`) for `us7032evb1` (`renesas/sh1`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:SH1_CLOCK]` Hardware/board configuration macros (`SH1_CLOCK`, `LED_STARTED`, `LED_HEAPALLOCATE`, `LED_IRQSENABLED`, `LED_STACKCREATED`, `LED_INIRQ` (+3 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh us7032evb1:nsh && make`
