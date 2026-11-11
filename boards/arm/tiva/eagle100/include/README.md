# `eagle100/include` Component (`boards/arm/tiva/eagle100/include`)

## Overview
Board-level public headers (`include`) for `eagle100` (`arm/tiva`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:SYSCON_RCC_XTAL]` Hardware/board configuration macros (`SYSCON_RCC_XTAL`, `XTAL_FREQUENCY`, `SYSCON_RCC_OSCSRC`, `SYSCON_RCC2_OSCSRC`, `OSCSRC_FREQUENCY`, `TIVA_SYSDIV` (+12 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh eagle100:nsh && make`
