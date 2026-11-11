# `bambino-200e` Board Support Package (`boards/arm/lpc43xx/bambino-200e`)

## Overview
Board Support Package (BSP) blueprint for `bambino-200e` (`arm` / `lpc43xx`). Coordinates board initialization, headers, and tooling across `include, kernel, scripts, src`. Includes build configurations: `knsh`, `max31855`, `netnsh`, `nsh`, `usbnsh`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `bambino-200e` (`arm/lpc43xx`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:BOARD_XTAL_FREQUENCY]` Hardware/board configuration macros (`BOARD_XTAL_FREQUENCY`, `BOARD_RTCCLK_FREQUENCY`, `BOARD_INTRCOSC_FREQUENCY`, `BOARD_PLL_MSEL`, `BOARD_PLL_NSEL`, `BOARD_PLL_PSEL` (+88 more)).
- [`kernel`](./kernel/README.md) - Protected-build userspace/kernel boundary module (`kernel`) for `bambino-200e` (`arm/lpc43xx`), providing userspace initialization and syscall/gate hooks across 1 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[lpc43_userspace.c:g_userspace_data]` Module symbol `g_userspace_data`.
- [`scripts`](./scripts/README.md) - Board support component `scripts` for `bambino-200e` (`arm/lpc43xx`), containing 1 source/script file(s) (`flash.sh`). Key symbols: `[flash.sh]` Shell script entry point `flash.sh`.
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `bambino-200e` (`arm/lpc43xx`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 8 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[CMakeLists.txt:board]` CMake build target source registration.
