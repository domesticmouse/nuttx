# `ci20/include` Component (`boards/mips/jz4780/ci20/include`)

## Overview
Board-level public headers (`include`) for `ci20` (`mips/jz4780`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:jz_usbhost_initialize]` Public declaration `jz_usbhost_initialize()`
- `[board.h:BOARD_ETH_FLG]` Hardware/board configuration macros (`BOARD_ETH_FLG`, `POWER_LED`)

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh ci20:nsh && make`
