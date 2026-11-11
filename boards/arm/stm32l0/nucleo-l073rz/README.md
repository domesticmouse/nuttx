# `nucleo-l073rz` Board Support Package (`boards/arm/stm32l0/nucleo-l073rz`)

## Overview
Board Support Package (BSP) blueprint for `nucleo-l073rz` (`arm` / `stm32l0`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`, `sx127x`, `usb-cdc`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `nucleo-l073rz` (`arm/stm32l0`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:stm32_usb_setpullup]` Public declaration `stm32_usb_setpullup()`, `[board.h:stm32_usb_pullup_enabled]` Public declaration `stm32_usb_pullup_enabled()`.
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `nucleo-l073rz` (`arm/stm32l0`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 8 source file(s). Key symbols: `[Make.defs:CSRCS]` Registered build sources in `Make.defs`, `[CMakeLists.txt:board]` CMake build target source registration.
