# `thingy53` Board Support Package (`boards/arm/nrf53/thingy53`)

## Overview
Board Support Package (BSP) blueprint for `thingy53` (`arm` / `nrf53`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `composite_cpuapp`, `nsh_cpuapp`, `nsh_cpunet`, `rgbled_cpuapp`, `rpmsghci_nimble_cpuapp`, `rpmsghci_sdc_cpunet` (+2 more).

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `thingy53` (`arm/nrf53`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:BOARD_SYSTICK_CLOCK]` Hardware/board configuration macros (`BOARD_SYSTICK_CLOCK`, `BOARD_OSC_XOSC32KI_INTCAP`, `BOARD_OSC_XOSC32MCAPS_CAP`, `BUTTON_BTN1`, `BUTTON_BTN2`, `BUTTON_BTN1_BIT` (+18 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `thingy53` (`arm/nrf53`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 13 source file(s). Key symbols: `[Make.defs:CSRCS]` Registered build sources in `Make.defs`, `[CMakeLists.txt:board]` CMake build target source registration.
