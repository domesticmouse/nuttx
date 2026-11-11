# `pnev5180b` Board Support Package (`boards/arm/lpc17xx_40xx/pnev5180b`)

## Overview
Board Support Package (BSP) blueprint for `pnev5180b` (`arm` / `lpc17xx_40xx`). Coordinates board initialization, headers, and tooling across `include, kernel, src`. Includes build configurations: `knsh`, `nsh`, `nsh-cdcecm`, `usbnsh`, `usbnsh-cdcecm`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `pnev5180b` (`arm/lpc17xx_40xx`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:lpc17_40_boardinitialize]` Public declaration `lpc17_40_boardinitialize()`, `[board.h:lpc17_40_led]` Public declaration `lpc17_40_led()`.
- [`kernel`](./kernel/README.md) - Protected-build userspace/kernel boundary module (`kernel`) for `pnev5180b` (`arm/lpc17xx_40xx`), providing userspace initialization and syscall/gate hooks across 1 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[lpc17_40_userspace.c:g_userspace_data]` Module symbol `g_userspace_data`.
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `pnev5180b` (`arm/lpc17xx_40xx`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 10 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[CMakeLists.txt:board]` CMake build target source registration.
