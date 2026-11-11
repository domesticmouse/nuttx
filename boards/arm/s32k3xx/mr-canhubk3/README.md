# `mr-canhubk3` Board Support Package (`boards/arm/s32k3xx/mr-canhubk3`)

## Overview
Board Support Package (BSP) blueprint for `mr-canhubk3` (`arm` / `s32k3xx`). Coordinates board initialization, headers, and tooling across `include, kernel, src`. Includes build configurations: `knsh`, `net`, `nsh`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `mr-canhubk3` (`arm/s32k3xx`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:BOARD_XTAL_FREQUENCY]` Hardware/board configuration macros (`BOARD_XTAL_FREQUENCY`, `MR_CANHUBK3_SYSCLK_FREQUENCY`, `HAVE_MX25L`, `HAVE_MX25L_LITTLEFS`, `HAVE_MX25L_NXFFS`, `HAVE_MX25L_CHARDEV` (+135 more)).
- [`kernel`](./kernel/README.md) - Protected-build userspace/kernel boundary module (`kernel`) for `mr-canhubk3` (`arm/s32k3xx`), providing userspace initialization and syscall/gate hooks across 1 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[s32k3xx_userspace.c:g_userspace_data]` Module symbol `g_userspace_data`.
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `mr-canhubk3` (`arm/s32k3xx`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 13 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[CMakeLists.txt:board]` CMake build target source registration.
