# `phy6222/include` Component (`boards/arm/phy62xx/phy6222/include`)

## Overview
Board-level public headers (`include`) for `phy6222` (`arm/phy62xx`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:HCLK_FREQUENCY]` Hardware/board configuration macros (`HCLK_FREQUENCY`)

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh phy6222:nsh && make`
