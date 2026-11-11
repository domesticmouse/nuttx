# `nrf9160-dk` Board Support Package (`boards/arm/nrf91/nrf9160-dk`)

## Overview
Board Support Package (BSP) blueprint for `nrf9160-dk` (`arm` / `nrf91`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `mcuboot_app`, `mcuboot_loader`, `miniboot_s`, `modem_ns`, `nsh`, `ostest_tickless`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `nrf9160-dk` (`arm/nrf91`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:BOARD_SYSTICK_CLOCK]` Hardware/board configuration macros (`BOARD_SYSTICK_CLOCK`, `BOARD_LED1`, `BOARD_LED2`, `BOARD_LED3`, `BOARD_LED4`, `BOARD_NLEDS` (+21 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `nrf9160-dk` (`arm/nrf91`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 7 source file(s). Key symbols: `[Make.defs:CSRCS]` Registered build sources in `Make.defs`, `[CMakeLists.txt:board]` CMake build target source registration.
