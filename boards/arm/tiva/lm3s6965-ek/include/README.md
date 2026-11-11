# `lm3s6965-ek/include` Component (`boards/arm/tiva/lm3s6965-ek/include`)

## Overview
Board-level public headers (`include`) for `lm3s6965-ek` (`arm/tiva`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:SYSCON_RCC_XTAL]` Hardware/board configuration macros (`SYSCON_RCC_XTAL`, `XTAL_FREQUENCY`, `SYSCON_RCC_OSCSRC`, `SYSCON_RCC2_OSCSRC`, `OSCSRC_FREQUENCY`, `TIVA_SYSDIV` (+12 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh lm3s6965-ek:nsh && make`
