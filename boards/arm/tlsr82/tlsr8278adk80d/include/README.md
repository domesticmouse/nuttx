# `tlsr8278adk80d/include` Component (`boards/arm/tlsr82/tlsr8278adk80d/include`)

## Overview
Board-level public headers (`include`) for `tlsr8278adk80d` (`arm/tlsr82`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:BOARD_NGPIO]` Hardware/board configuration macros (`BOARD_NGPIO`, `BOARD_GPIO0_PIN`, `BOARD_GPIO0_TYPE`, `BOARD_GPIO1_PIN`, `BOARD_GPIO1_TYPE`, `BOARD_GPIO2_PIN` (+33 more))

## Invariants
- `[board.h:#error]` Compile-time guard: `BOARD_NGPIO max value is 8`

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh tlsr8278adk80d:nsh && make`
