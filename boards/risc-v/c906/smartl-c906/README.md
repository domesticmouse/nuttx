# `smartl-c906` Board Support Package (`boards/risc-v/c906/smartl-c906`)

## Overview
Board Support Package (BSP) blueprint for `smartl-c906` (`risc-v` / `c906`). Coordinates board initialization, headers, and tooling across `include, kernel, src`. Includes build configurations: `elf`, `fpu`, `knsh`, `module`, `nsh`, `sotest`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `smartl-c906` (`risc-v/c906`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:c906_boardinitialize]` Public declaration `c906_boardinitialize()`.
- [`kernel`](./kernel/README.md) - Protected-build userspace/kernel boundary module (`kernel`) for `smartl-c906` (`risc-v/c906`), providing userspace initialization and syscall/gate hooks across 1 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[c906_userspace.c:g_userspace_data]` Module symbol `g_userspace_data`.
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `smartl-c906` (`risc-v/c906`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 4 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[smartl-c906.h:c906_bringup]` Public declaration `c906_bringup()`.
