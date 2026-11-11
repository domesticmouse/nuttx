# `canmv230/include` Component (`boards/risc-v/k230/canmv230/include`)

## Overview
Board-level public headers (`include`) for `canmv230` (`risc-v/k230`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 2 header file(s).

## Interface
- `[board.h:k230_boardinitialize]` Public declaration `k230_boardinitialize()`
- `[board.h:LED_STARTED]` Hardware/board configuration macros (`LED_STARTED`, `LED_HEAPALLOCATE`, `LED_IRQSENABLED`, `LED_STACKCREATED`, `LED_INIRQ`, `LED_SIGNAL` (+3 more))
- `[board_memorymap.h:KFLASH_START]` Hardware/board configuration macros (`KFLASH_START`, `KFLASH_SIZE`, `KSRAM_START`, `KSRAM_SIZE`, `KSRAM_END`, `PGPOOL_START` (+6 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh canmv230:nsh && make`
