# `olimex-lpc2378/include` Component (`boards/arm/lpc2378/olimex-lpc2378/include`)

## Overview
Board-level public headers (`include`) for `olimex-lpc2378` (`arm/lpc2378`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:FOSC]` Hardware/board configuration macros (`FOSC`, `FCCO`, `CCLK`, `PLL_M`, `PLL_N`, `CCLK_DIV` (+10 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh olimex-lpc2378:nsh && make`
