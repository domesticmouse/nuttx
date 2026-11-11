# `samv71-xult` Board Support Package (`boards/arm/samv7/samv71-xult`)

## Overview
Board Support Package (BSP) blueprint for `samv71-xult` (`arm` / `samv7`). Coordinates board initialization, headers, and tooling across `include, kernel, src`. Includes build configurations: `knsh`, `mcuboot-loader`, `mcuboot-slot-confirm`, `mcuboot-swap-test`, `mcuboot-update-agent`, `module` (+8 more).

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `samv71-xult` (`arm/samv7`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:sam_lcdclear]` Public declaration `sam_lcdclear()`, `[board.h:BOARD_HAVE_SLOWXTAL]` Hardware/board configuration macros (`BOARD_HAVE_SLOWXTAL`, `BOARD_SLOWCLK_FREQUENCY`, `BOARD_MAINOSC_FREQUENCY`, `BOARD_CKGR_MOR_MOSCXTST`, `BOARD_CKGR_MOR_MOSCXTENBY`, `BOARD_CKGR_PLLAR_STMODE` (+43 more)).
- [`kernel`](./kernel/README.md) - Protected-build userspace/kernel boundary module (`kernel`) for `samv71-xult` (`arm/samv7`), providing userspace initialization and syscall/gate hooks across 1 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[sam_userspace.c:g_userspace_data]` Module symbol `g_userspace_data`.
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `samv71-xult` (`arm/samv7`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 24 source file(s). Key symbols: `[Make.defs:CSRCS]` Registered build sources in `Make.defs`, `[atmxt-xpro.h:atmxt_config_s]` Type definition `atmxt_config_s`.
