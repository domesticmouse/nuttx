# `nrf52840-dk` Board Support Package (`boards/arm/nrf52/nrf52840-dk`)

## Overview
Board Support Package (BSP) blueprint for `nrf52840-dk` (`arm` / `nrf52`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `cdcacm`, `composite`, `highpri`, `ieee802154_6lowpan`, `ieee802154_mac`, `jumbo` (+8 more).

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `nrf52840-dk` (`arm/nrf52`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:BOARD_SYSTICK_CLOCK]` Hardware/board configuration macros (`BOARD_SYSTICK_CLOCK`, `BOARD_LED1`, `BOARD_LED2`, `BOARD_LED3`, `BOARD_LED4`, `BOARD_NLEDS` (+46 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `nrf52840-dk` (`arm/nrf52`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 19 source file(s). Key symbols: `[Make.defs:CSRCS]` Registered build sources in `Make.defs`, `[CMakeLists.txt:board]` CMake build target source registration.
