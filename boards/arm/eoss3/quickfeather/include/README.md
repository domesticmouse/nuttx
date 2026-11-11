# `quickfeather/include` Component (`boards/arm/eoss3/quickfeather/include`)

## Overview
Board-level public headers (`include`) for `quickfeather` (`arm/eoss3`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:BOARD_HCLK_FREQUENCY]` Hardware/board configuration macros (`BOARD_HCLK_FREQUENCY`, `BOARD_CPU_FREQUENCY`, `LED_STARTED`, `LED_HEAPALLOCATE`, `LED_IRQSENABLED`, `LED_STACKCREATED` (+9 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh quickfeather:nsh && make`
