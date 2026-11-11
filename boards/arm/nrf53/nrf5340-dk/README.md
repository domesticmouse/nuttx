# `nrf5340-dk` Board Support Package (`boards/arm/nrf53/nrf5340-dk`)

## Overview
Board Support Package (BSP) blueprint for `nrf5340-dk` (`arm` / `nrf53`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `adc_cpuapp`, `buttons_cpuapp`, `composite_cpuapp`, `ieee802154_6lowpan_cpunet`, `ieee802154_mac_cpunet`, `mcuboot_app_cpuapp` (+15 more).

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `nrf5340-dk` (`arm/nrf53`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:BOARD_SYSTICK_CLOCK]` Hardware/board configuration macros (`BOARD_SYSTICK_CLOCK`, `BOARD_OSC_XOSC32KI_INTCAP`, `BOARD_OSC_XOSC32MCAPS_CAP`, `BOARD_LED1`, `BOARD_LED2`, `BOARD_LED3` (+43 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `nrf5340-dk` (`arm/nrf53`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 14 source file(s). Key symbols: `[Make.defs:CSRCS]` Registered build sources in `Make.defs`, `[CMakeLists.txt:board]` CMake build target source registration.
