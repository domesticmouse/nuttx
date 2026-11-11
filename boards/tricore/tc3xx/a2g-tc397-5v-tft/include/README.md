# `a2g-tc397-5v-tft/include` Component (`boards/tricore/tc3xx/a2g-tc397-5v-tft/include`)

## Overview
Board-level public headers (`include`) for `a2g-tc397-5v-tft` (`tricore/tc3xx`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 2 header file(s).

## Interface
- `[board.h]` Board header declarations `board.h`
- `[board_memorymap.h:BANKA_CORE0_PFLASH_KERNEL_START]` Hardware/board configuration macros (`BANKA_CORE0_PFLASH_KERNEL_START`, `BANKA_CORE0_PFLASH_KERNEL_SIZE`, `BANKA_CORE0_PFLASH_USER_START`, `BANKA_CORE0_PFLASH_USER_SIZE`, `BANKA_CORE1_PFLASH_KERNEL_START`, `BANKA_CORE1_PFLASH_KERNEL_SIZE` (+245 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh a2g-tc397-5v-tft:nsh && make`
