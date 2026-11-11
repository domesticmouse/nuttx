# `dk-tm4c129x/include` Component (`boards/arm/tiva/dk-tm4c129x/include`)

## Overview
Board-level public headers (`include`) for `dk-tm4c129x` (`arm/tiva`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:tiva_tmp100_initialize]` Public declaration `tiva_tmp100_initialize()`
- `[board.h:SYSCON_RCC_XTAL]` Hardware/board configuration macros (`SYSCON_RCC_XTAL`, `XTAL_FREQUENCY`, `PIOSC_FREQUENCY`, `RTCOSC_FREQUENCY`, `LFIOSC_FREQUENCY`, `BOARD_PLL_MINT` (+52 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh dk-tm4c129x:nsh && make`
