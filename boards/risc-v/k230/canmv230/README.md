# `canmv230` Board Support Package (`boards/risc-v/k230/canmv230`)

## Overview
Board Support Package (BSP) blueprint for `canmv230` (`risc-v` / `k230`). Coordinates board initialization, headers, and tooling across `include, kernel, src`. Includes build configurations: `knsh`, `master`, `nsbi`, `nsh`, `pnsh`, `remote`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `canmv230` (`risc-v/k230`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 2 header file(s). Key symbols: `[board.h:k230_boardinitialize]` Public declaration `k230_boardinitialize()`, `[board.h:LED_STARTED]` Hardware/board configuration macros (`LED_STARTED`, `LED_HEAPALLOCATE`, `LED_IRQSENABLED`, `LED_STACKCREATED`, `LED_INIRQ`, `LED_SIGNAL` (+3 more)).
- [`kernel`](./kernel/README.md) - Protected-build userspace/kernel boundary module (`kernel`) for `canmv230` (`risc-v/k230`), providing userspace initialization and syscall/gate hooks across 1 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[k230_userspace.c:g_userspace_data]` Module symbol `g_userspace_data`.
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `canmv230` (`risc-v/k230`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 3 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[CMakeLists.txt:board]` CMake build target source registration.
