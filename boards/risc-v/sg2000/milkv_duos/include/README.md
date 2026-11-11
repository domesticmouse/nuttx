# `milkv_duos/include` Component (`boards/risc-v/sg2000/milkv_duos/include`)

## Overview
Board-level public headers (`include`) for `milkv_duos` (`risc-v/sg2000`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 2 header file(s).

## Interface
- `[board.h:sg2000_boardinitialize]` Public declaration `sg2000_boardinitialize()`
- `[board.h:LED_STARTED]` Hardware/board configuration macros (`LED_STARTED`, `LED_HEAPALLOCATE`, `LED_IRQSENABLED`, `LED_STACKCREATED`, `LED_INIRQ`, `LED_SIGNAL` (+3 more))
- `[board_memorymap.h:SG2000_DDR_BASE]` Hardware/board configuration macros (`SG2000_DDR_BASE`, `SG2000_DDR_SIZE`, `KFLASH_START`, `KFLASH_SIZE`, `KSRAM_START`, `KSRAM_SIZE` (+6 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh milkv_duos:nsh && make`
