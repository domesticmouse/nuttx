# `tm4c123g-launchpad/include` Component (`boards/arm/tiva/tm4c123g-launchpad/include`)

## Overview
Board-level public headers (`include`) for `tm4c123g-launchpad` (`arm/tiva`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:SYSCON_RCC_XTAL]` Hardware/board configuration macros (`SYSCON_RCC_XTAL`, `XTAL_FREQUENCY`, `SYSCON_RCC_OSCSRC`, `SYSCON_RCC2_OSCSRC`, `OSCSRC_FREQUENCY`, `TIVA_SYSDIV` (+29 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh tm4c123g-launchpad:nsh && make`
