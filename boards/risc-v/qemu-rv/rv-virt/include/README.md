# `rv-virt/include` Component (`boards/risc-v/qemu-rv/rv-virt/include`)

## Overview
Board-level public headers (`include`) for `rv-virt` (`risc-v/qemu-rv`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 2 header file(s).

## Interface
- `[board.h:qemu_rv_boardinitialize]` Public declaration `qemu_rv_boardinitialize()`
- `[board.h:BOARD_LED1_BIT]` Hardware/board configuration macros (`BOARD_LED1_BIT`, `BOARD_LED2_BIT`, `BOARD_LED3_BIT`, `LED_STARTED`, `LED_HEAPALLOCATE`, `LED_IRQSENABLED` (+6 more))
- `[board_memorymap.h:QEMURV_DDR_BASE]` Hardware/board configuration macros (`QEMURV_DDR_BASE`, `QEMURV_DDR_SIZE`, `KFLASH_START`, `KFLASH_SIZE`, `KSRAM_START`, `KSRAM_SIZE` (+8 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh rv-virt:nsh && make`
