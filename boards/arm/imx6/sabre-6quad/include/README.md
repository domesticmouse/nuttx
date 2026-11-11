# `sabre-6quad/include` Component (`boards/arm/imx6/sabre-6quad/include`)

## Overview
Board-level public headers (`include`) for `sabre-6quad` (`arm/imx6`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 2 header file(s).

## Interface
- `[board.h:BOARD_CPUXTAL_FREQUENCY]` Hardware/board configuration macros (`BOARD_CPUXTAL_FREQUENCY`, `BAORD_RTCXTAL_FREQUENCY`, `BOARD_CPU_FREQUENCY`, `BOARD_LED`, `BOARD_NLEDS`, `BOARD_LED_BIT` (+10 more))
- `[board_memorymap.h]` Board header declarations `board_memorymap.h`

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh sabre-6quad:nsh && make`
