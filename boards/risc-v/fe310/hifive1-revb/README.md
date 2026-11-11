# `hifive1-revb` Board Support Package (`boards/risc-v/fe310/hifive1-revb`)

## Overview
Board Support Package (BSP) blueprint for `hifive1-revb` (`risc-v` / `fe310`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `hifive1-revb` (`risc-v/fe310`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:fe310_boardinitialize]` Public declaration `fe310_boardinitialize()`, `[board.h:NUM_BUTTONS]` Hardware/board configuration macros (`NUM_BUTTONS`, `LED_STARTED`, `LED_HEAPALLOCATE`, `LED_IRQSENABLED`, `LED_STACKCREATED`, `LED_INIRQ` (+4 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `hifive1-revb` (`risc-v/fe310`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 5 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[CMakeLists.txt:board]` CMake build target source registration.
