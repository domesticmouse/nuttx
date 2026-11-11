# `demo9s12ne64/include` Component (`boards/hc/m9s12/demo9s12ne64/include`)

## Overview
Board-level public headers (`include`) for `demo9s12ne64` (`hc/m9s12`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:HCS12_OSCCLK]` Hardware/board configuration macros (`HCS12_OSCCLK`, `HCS12_SYNR_VALUE`, `HCS12_REFDV_VALUE`, `HCS12_PLLCLK`, `HCS12_BUSCLK`, `LED_STARTED` (+7 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh demo9s12ne64:ostest && make`
