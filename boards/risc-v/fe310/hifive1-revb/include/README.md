# `hifive1-revb/include` Component (`boards/risc-v/fe310/hifive1-revb/include`)

## Overview
Board-level public headers (`include`) for `hifive1-revb` (`risc-v/fe310`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:fe310_boardinitialize]` Public declaration `fe310_boardinitialize()`
- `[board.h:NUM_BUTTONS]` Hardware/board configuration macros (`NUM_BUTTONS`, `LED_STARTED`, `LED_HEAPALLOCATE`, `LED_IRQSENABLED`, `LED_STACKCREATED`, `LED_INIRQ` (+4 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh hifive1-revb:nsh && make`
