# `rx65n/include` Component (`boards/renesas/rx65n/rx65n/include`)

## Overview
Board-level public headers (`include`) for `rx65n` (`renesas/rx65n`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:RX_FCLK]` Hardware/board configuration macros (`RX_FCLK`, `RX_ICLK`, `RX_PCLKA`, `RX_PCLKB`, `RX_PCLKC`, `RX_PCLKD` (+13 more))

## Invariants
- `[board.h:#error]` Compile-time guard: `Please definition RX_RESONATOR in board.h`
- `[board.h:#error]` Compile-time guard: `LEDs are not defined.`

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh rx65n:nsh && make`
