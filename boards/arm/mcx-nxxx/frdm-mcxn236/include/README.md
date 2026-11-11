# `frdm-mcxn236/include` Component (`boards/arm/mcx-nxxx/frdm-mcxn236/include`)

## Overview
Board-level public headers (`include`) for `frdm-mcxn236` (`arm/mcx-nxxx`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:nxxx_boardinitialize]` Public declaration `nxxx_boardinitialize()`
- `[board.h:PORT_LPUART4_RX]` Hardware/board configuration macros (`PORT_LPUART4_RX`, `PORT_LPUART4_TX`, `PORT_LPI2C0_SCL`, `PORT_LPI2C0_SDA`)

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh frdm-mcxn236:nsh && make`
