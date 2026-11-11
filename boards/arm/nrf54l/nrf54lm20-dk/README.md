# `nrf54lm20-dk` Board Support Package (`boards/arm/nrf54l/nrf54lm20-dk`)

## Overview
Board Support Package (BSP) blueprint for `nrf54lm20-dk` (`arm` / `nrf54l`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `ieee802154_6lowpan`, `ieee802154_mac`, `nsh`, `sdc`, `usbnsh`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `nrf54lm20-dk` (`arm/nrf54l`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:BOARD_SYSTICK_CLOCK]` Hardware/board configuration macros (`BOARD_SYSTICK_CLOCK`, `BOARD_HFXO_CAPACITANCE`, `BOARD_LED1`, `BOARD_LED2`, `BOARD_LED3`, `BOARD_LED4` (+15 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `nrf54lm20-dk` (`arm/nrf54l`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 6 source file(s). Key symbols: `[Make.defs:CSRCS]` Registered build sources in `Make.defs`, `[CMakeLists.txt:board]` CMake build target source registration.
