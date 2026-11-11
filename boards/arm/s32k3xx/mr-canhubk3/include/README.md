# `mr-canhubk3/include` Component (`boards/arm/s32k3xx/mr-canhubk3/include`)

## Overview
Board-level public headers (`include`) for `mr-canhubk3` (`arm/s32k3xx`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:BOARD_XTAL_FREQUENCY]` Hardware/board configuration macros (`BOARD_XTAL_FREQUENCY`, `MR_CANHUBK3_SYSCLK_FREQUENCY`, `HAVE_MX25L`, `HAVE_MX25L_LITTLEFS`, `HAVE_MX25L_NXFFS`, `HAVE_MX25L_CHARDEV` (+135 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh mr-canhubk3:nsh && make`
