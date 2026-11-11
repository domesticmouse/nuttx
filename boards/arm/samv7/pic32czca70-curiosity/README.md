# `pic32czca70-curiosity` Board Support Package (`boards/arm/samv7/pic32czca70-curiosity`)

## Overview
Board Support Package (BSP) blueprint for `pic32czca70-curiosity` (`arm` / `samv7`). Coordinates board initialization, headers, and tooling across `include, kernel, src`. Includes build configurations: `max`, `nsh`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `pic32czca70-curiosity` (`arm/samv7`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:BOARD_HAVE_SLOWXTAL]` Hardware/board configuration macros (`BOARD_HAVE_SLOWXTAL`, `BOARD_SLOWCLK_FREQUENCY`, `BOARD_MAINOSC_FREQUENCY`, `BOARD_CKGR_MOR_MOSCXTST`, `BOARD_CKGR_MOR_MOSCXTENBY`, `BOARD_CKGR_PLLAR_STMODE` (+34 more)).
- [`kernel`](./kernel/README.md) - Protected-build userspace/kernel boundary module (`kernel`) for `pic32czca70-curiosity` (`arm/samv7`), providing userspace initialization and syscall/gate hooks across 1 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[sam_userspace.c]` Translation unit `sam_userspace.c`.
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `pic32czca70-curiosity` (`arm/samv7`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 10 source file(s). Key symbols: `[Make.defs:CSRCS]` Registered build sources in `Make.defs`, `[sam_board.h:sam_usbinitialize]` Public declaration `sam_usbinitialize()`.
