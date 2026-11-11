# `tm4c129e-launchpad/include` Component (`boards/arm/tiva/tm4c129e-launchpad/include`)

## Overview
Board-level public headers (`include`) for `tm4c129e-launchpad` (`arm/tiva`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:SYSCON_RCC_XTAL]` Hardware/board configuration macros (`SYSCON_RCC_XTAL`, `XTAL_FREQUENCY`, `PIOSC_FREQUENCY`, `RTCOSC_FREQUENCY`, `LFIOSC_FREQUENCY`, `BOARD_PLL_MINT` (+37 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh tm4c129e-launchpad:nsh && make`
