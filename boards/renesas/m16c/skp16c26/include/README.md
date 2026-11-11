# `skp16c26/include` Component (`boards/renesas/m16c/skp16c26/include`)

## Overview
Board-level public headers (`include`) for `skp16c26` (`renesas/m16c`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:M16C_XIN_FREQ]` Hardware/board configuration macros (`M16C_XIN_FREQ`, `M16C_DEFAULT_IPL`, `M16C_TA0_PRIO`, `LED_STARTED`, `LED_HEAPALLOCATE`, `LED_IRQSENABLED` (+8 more))

## Invariants
- `[board.h:#error]` Compile-time guard: `UART1/2 should not be used on SKP16C26`

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh skp16c26:ostest && make`
