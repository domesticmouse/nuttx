# `star64/include` Component (`boards/risc-v/jh7110/star64/include`)

## Overview
Board-level public headers (`include`) for `star64` (`risc-v/jh7110`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 2 header file(s).

## Interface
- `[board.h:jh7110_boardinitialize]` Public declaration `jh7110_boardinitialize()`
- `[board.h:LED_STARTED]` Hardware/board configuration macros (`LED_STARTED`, `LED_HEAPALLOCATE`, `LED_IRQSENABLED`, `LED_STACKCREATED`, `LED_INIRQ`, `LED_SIGNAL` (+3 more))
- `[board_memorymap.h:JH7110_DDR_BASE]` Hardware/board configuration macros (`JH7110_DDR_BASE`, `JH7110_DDR_SIZE`, `KFLASH_START`, `KFLASH_SIZE`, `KSRAM_START`, `KSRAM_SIZE` (+6 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh star64:nsh && make`
