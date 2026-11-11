# `ntosd-dm320/include` Component (`boards/arm/dm320/ntosd-dm320/include`)

## Overview
Board-level public headers (`include`) for `ntosd-dm320` (`arm/dm320`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:DM320_ARM_CLOCK]` Hardware/board configuration macros (`DM320_ARM_CLOCK`, `DM320_SDR_CLOCK`, `DM320_DSP_CLOCK`, `DM320_AXL_CLOCK`, `DM320_AHB_CLOCK`, `CONFIG_DM320_UARTPPLIN` (+40 more))

## Invariants
- `[board.h:#error]` Compile-time guard: `Invalid setting for CONFIG_RAM_START`

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh ntosd-dm320:nsh && make`
