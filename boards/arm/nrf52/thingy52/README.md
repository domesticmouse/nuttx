# `thingy52` Board Support Package (`boards/arm/nrf52/thingy52`)

## Overview
Board Support Package (BSP) blueprint for `thingy52` (`arm` / `nrf52`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`, `thingy_nimble`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `thingy52` (`arm/nrf52`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:BOARD_SYSTICK_CLOCK]` Hardware/board configuration macros (`BOARD_SYSTICK_CLOCK`, `BUTTON_BTN1`, `NUM_BUTTONS`, `BUTTON_BTN1_BIT`, `BOARD_UART0_RX_PIN`, `BOARD_UART0_TX_PIN` (+3 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `thingy52` (`arm/nrf52`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 8 source file(s). Key symbols: `[Make.defs:CSRCS]` Registered build sources in `Make.defs`, `[CMakeLists.txt:board]` CMake build target source registration.
