# `avr32dev1/include` Component (`boards/avr/at32uc3/avr32dev1/include`)

## Overview
Board-level public headers (`include`) for `avr32dev1` (`avr/at32uc3`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:AVR32_FRCOSC]` Hardware/board configuration macros (`AVR32_FRCOSC`, `AVR32_FOSC32`, `AVR32_OSC32STARTUP`, `AVR32_FOSC0`, `AVR32_OSC0STARTUP`, `AVR32_CLOCK_PLL0_OSC0` (+32 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh avr32dev1:nsh && make`
