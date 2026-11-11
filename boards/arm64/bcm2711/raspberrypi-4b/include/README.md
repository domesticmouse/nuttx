# `raspberrypi-4b/include` Component (`boards/arm64/bcm2711/raspberrypi-4b/include`)

## Overview
Board-level public headers (`include`) for `raspberrypi-4b` (`arm64/bcm2711`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:STATUS_LED]` Hardware/board configuration macros (`STATUS_LED`, `POWER_LED`, `LED_STARTED`, `LED_HEAPALLOCATE`, `LED_IRQSENABLED`, `LED_STACKCREATED` (+8 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh raspberrypi-4b:nsh && make`
