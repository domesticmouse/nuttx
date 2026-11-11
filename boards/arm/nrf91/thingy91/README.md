# `thingy91` Board Support Package (`boards/arm/nrf91/thingy91`)

## Overview
Board Support Package (BSP) blueprint for `thingy91` (`arm` / `nrf91`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh_nrf52`, `nsh_rtt`, `thingy91_rtt`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `thingy91` (`arm/nrf91`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:BOARD_SYSTICK_CLOCK]` Hardware/board configuration macros (`BOARD_SYSTICK_CLOCK`, `BUTTON_BTN1`, `NUM_BUTTONS`, `BUTTON_BTN1_BIT`, `BOARD_UART0_RX_PIN`, `BOARD_UART0_TX_PIN` (+11 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `thingy91` (`arm/nrf91`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 9 source file(s). Key symbols: `[Make.defs:CSRCS]` Registered build sources in `Make.defs`, `[CMakeLists.txt:board]` CMake build target source registration.
