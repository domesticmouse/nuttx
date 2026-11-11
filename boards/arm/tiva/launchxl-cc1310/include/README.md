# `launchxl-cc1310/include` Component (`boards/arm/tiva/launchxl-cc1310/include`)

## Overview
Board-level public headers (`include`) for `launchxl-cc1310` (`arm/tiva`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:SYSCLK_FREQUENCY]` Hardware/board configuration macros (`SYSCLK_FREQUENCY`, `PCLK_FREQUENCY`, `BOARD_GLED`, `BOARD_RLED`, `BOARD_NLEDS`, `BOARD_GLED_BIT` (+16 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh launchxl-cc1310:nsh && make`
