# `qemu-armv7r/include` Component (`boards/arm/qemu/qemu-armv7r/include`)

## Overview
Board-level public headers (`include`) for `qemu-armv7r` (`arm/qemu`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 2 header file(s).

## Interface
- `[board.h]` Board header declarations `board.h`
- `[board_memorymap.h:QEMU_DDR_BASE]` Hardware/board configuration macros (`QEMU_DDR_BASE`, `QEMU_DDR_SIZE`, `KFLASH_START`, `KFLASH_SIZE`, `KSRAM_START`, `KSRAM_SIZE` (+9 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh qemu-armv7r:nsh && make`
