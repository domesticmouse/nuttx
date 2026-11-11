# `thingy91-nrf52` Board Support Package (`boards/arm/nrf52/thingy91-nrf52`)

## Overview
Board Support Package (BSP) blueprint for `thingy91-nrf52` (`arm` / `nrf52`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `usbnsh`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `thingy91-nrf52` (`arm/nrf52`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:BOARD_SYSTICK_CLOCK]` Hardware/board configuration macros (`BOARD_SYSTICK_CLOCK`, `BOARD_NLEDS`, `NUM_BUTTONS`, `BOARD_UART0_RX_PIN`, `BOARD_UART0_TX_PIN`).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `thingy91-nrf52` (`arm/nrf52`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 5 source file(s). Key symbols: `[Make.defs:CSRCS]` Registered build sources in `Make.defs`, `[CMakeLists.txt:board]` CMake build target source registration.
