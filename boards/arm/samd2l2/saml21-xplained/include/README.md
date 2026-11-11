# `saml21-xplained/include` Component (`boards/arm/samd2l2/saml21-xplained/include`)

## Overview
Board-level public headers (`include`) for `saml21-xplained` (`arm/samd2l2`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:BOARD_XOSC_FREQUENCY]` Hardware/board configuration macros (`BOARD_XOSC_FREQUENCY`, `BOARD_XOSC_STARTUPTIME`, `BOARD_XOSC_ISCRYSTAL`, `BOARD_XOSC_AMPGC`, `BOARD_XOSC_ONDEMAND`, `BOARD_XOSC32K_ENABLE` (+141 more))

## Invariants
- `[board.h:#error]` Compile-time guard: `OSC16M operating frequency not defined (CONFIG_SAML21_XPLAINED_OSC16M_*MHZ)`
- `[board.h:#error]` Compile-time guard: `DFLL mode not provided`

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh saml21-xplained:nsh && make`
