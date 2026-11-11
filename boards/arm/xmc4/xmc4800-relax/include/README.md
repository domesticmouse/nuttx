# `xmc4800-relax/include` Component (`boards/arm/xmc4/xmc4800-relax/include`)

## Overview
Board-level public headers (`include`) for `xmc4800-relax` (`arm/xmc4`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:BOARD_FCPU_144MHZ]` Hardware/board configuration macros (`BOARD_FCPU_144MHZ`, `WDT_CLKSRC_FOFI`, `WDT_CLKSRC_FSTDY`, `WDT_CLKSRC_FPLL`, `EXT_CLKSRC_FSYS`, `EXT_CLKSRC_FUSB` (+101 more))

## Invariants
- `[board.h:#error]` Compile-time guard: `Illegal or Unsupported CPU Frequency`
- `[board.h:#error]` Compile-time guard: `VCO freq must be >= 260 MHz`

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh xmc4800-relax:nsh && make`
