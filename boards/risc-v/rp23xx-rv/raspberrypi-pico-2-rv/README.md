# `raspberrypi-pico-2-rv` Board Support Package (`boards/risc-v/rp23xx-rv/raspberrypi-pico-2-rv`)

## Overview
Board Support Package (BSP) blueprint for `raspberrypi-pico-2-rv` (`risc-v` / `rp23xx-rv`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`, `nsh-smp`, `usbnsh`, `usbnsh-smp`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `raspberrypi-pico-2-rv` (`risc-v/rp23xx-rv`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 5 header file(s). Key symbols: `[board.h:rp23xx_boardearlyinitialize]` Public declaration `rp23xx_boardearlyinitialize()`, `[board.h:rp23xx_boardinitialize]` Public declaration `rp23xx_boardinitialize()`.
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `raspberrypi-pico-2-rv` (`risc-v/rp23xx-rv`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 7 source file(s). Key symbols: `[Make.defs:CSRCS]` Registered build sources in `Make.defs`, `[CMakeLists.txt:board]` CMake build target source registration.
