# `rv32m1-vega` Board Support Package (`boards/risc-v/rv32m1/rv32m1-vega`)

## Overview
Board Support Package (BSP) blueprint for `rv32m1-vega` (`risc-v` / `rv32m1`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `buttons`, `nsh`, `nsh-itcm`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `rv32m1-vega` (`risc-v/rv32m1`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:rv32m1_boardinitialize]` Public declaration `rv32m1_boardinitialize()`, `[board.h:LED_STARTED]` Hardware/board configuration macros (`LED_STARTED`, `LED_HEAPALLOCATE`, `LED_IRQSENABLED`, `LED_STACKCREATED`, `LED_INIRQ`, `LED_SIGNAL` (+11 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `rv32m1-vega` (`risc-v/rv32m1`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 5 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[rv32m1-vega.h:rv32m1_bringup]` Public declaration `rv32m1_bringup()`.
