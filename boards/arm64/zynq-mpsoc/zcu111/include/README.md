# `zcu111/include` Component (`boards/arm64/zynq-mpsoc/zcu111/include`)

## Overview
Board-level public headers (`include`) for `zcu111` (`arm64/zynq-mpsoc`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:BOARD_LED1]` Hardware/board configuration macros (`BOARD_LED1`, `BOARD_NLEDS`, `BOARD_LED1_BIT`, `LED_STARTED`, `LED_HEAPALLOCATE`, `LED_IRQSENABLED` (+10 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh zcu111:nsh && make`
