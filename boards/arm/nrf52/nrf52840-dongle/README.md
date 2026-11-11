# `nrf52840-dongle` Board Support Package (`boards/arm/nrf52/nrf52840-dongle`)

## Overview
Board Support Package (BSP) blueprint for `nrf52840-dongle` (`arm` / `nrf52`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `ieee802154_mac`, `nsh`, `usbnsh`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `nrf52840-dongle` (`arm/nrf52`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:BOARD_SYSTICK_CLOCK]` Hardware/board configuration macros (`BOARD_SYSTICK_CLOCK`, `BOARD_LED1`, `BOARD_NLEDS`, `BOARD_LED1_BIT`, `LED_STARTED`, `LED_HEAPALLOCATE` (+11 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `nrf52840-dongle` (`arm/nrf52`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 7 source file(s). Key symbols: `[Make.defs:CSRCS]` Registered build sources in `Make.defs`, `[CMakeLists.txt:board]` CMake build target source registration.
