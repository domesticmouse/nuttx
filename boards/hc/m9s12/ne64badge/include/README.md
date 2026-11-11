# `ne64badge/include` Component (`boards/hc/m9s12/ne64badge/include`)

## Overview
Board-level public headers (`include`) for `ne64badge` (`hc/m9s12`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:HCS12_OSCCLK]` Hardware/board configuration macros (`HCS12_OSCCLK`, `HCS12_SYNR_VALUE`, `HCS12_REFDV_VALUE`, `HCS12_PLLCLK`, `HCS12_BUSCLK`, `LED_STARTED` (+9 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh ne64badge:ostest && make`
