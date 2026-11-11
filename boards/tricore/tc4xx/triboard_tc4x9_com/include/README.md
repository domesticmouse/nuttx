# `triboard_tc4x9_com/include` Component (`boards/tricore/tc4xx/triboard_tc4x9_com/include`)

## Overview
Board-level public headers (`include`) for `triboard_tc4x9_com` (`tricore/tc4xx`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 2 header file(s).

## Interface
- `[board.h]` Board header declarations `board.h`
- `[board_memorymap.h:BANKA_CORE0_PFLASH_KERNEL_START]` Hardware/board configuration macros (`BANKA_CORE0_PFLASH_KERNEL_START`, `BANKA_CORE0_PFLASH_KERNEL_SIZE`, `BANKA_CORE0_PFLASH_USER_START`, `BANKA_CORE0_PFLASH_USER_SIZE`, `BANKA_CORE1_PFLASH_KERNEL_START`, `BANKA_CORE1_PFLASH_KERNEL_SIZE` (+331 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh triboard_tc4x9_com:nsh && make`
