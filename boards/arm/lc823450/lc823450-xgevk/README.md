# `lc823450-xgevk` Board Support Package (`boards/arm/lc823450/lc823450-xgevk`)

## Overview
Board Support Package (BSP) blueprint for `lc823450-xgevk` (`arm` / `lc823450`). Coordinates board initialization, headers, and tooling across `include, kernel, src`. Includes build configurations: `audio`, `bt`, `elf`, `ipl2`, `knsh`, `kostest` (+5 more).

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `lc823450-xgevk` (`arm/lc823450`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:up_init_default_mux]` Public declaration `up_init_default_mux()`, `[board.h:LED_STARTED]` Hardware/board configuration macros (`LED_STARTED`, `LED_HEAPALLOCATE`, `LED_IRQSENABLED`, `LED_STACKCREATED`, `LED_INIRQ`, `LED_SIGNAL` (+4 more)).
- [`kernel`](./kernel/README.md) - Protected-build userspace/kernel boundary module (`kernel`) for `lc823450-xgevk` (`arm/lc823450`), providing userspace initialization and syscall/gate hooks across 1 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[lc823450_userspace.c:g_userspace_data]` Module symbol `g_userspace_data`.
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `lc823450-xgevk` (`arm/lc823450`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 15 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[lc823450-xgevk.h:lc823450_adc_setup]` Public declaration `lc823450_adc_setup()`.
