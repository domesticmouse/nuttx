# `fvp-armv8r` Board Support Package (`boards/arm64/fvp-v8r/fvp-armv8r`)

## Overview
Board Support Package (BSP) blueprint for `fvp-armv8r` (`arm64` / `fvp-v8r`). Coordinates board initialization, headers, and tooling across `include, kernel, src`. Includes build configurations: `citest`, `citest_smp`, `nsh`, `nsh_smp`, `pnsh`, `pnsh_smp`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `fvp-armv8r` (`arm64/fvp-v8r`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 2 header file(s). Key symbols: `[board.h]` Board header declarations `board.h`, `[board_memorymap.h:KTEXT_SIZE]` Hardware/board configuration macros (`KTEXT_SIZE`, `KSRAM_SIZE`, `UTEXT_SIZE`, `USRAM_SIZE`, `KTEXT_START`, `KTEXT_END` (+6 more)).
- [`kernel`](./kernel/README.md) - Protected-build userspace/kernel boundary module (`kernel`) for `fvp-armv8r` (`arm64/fvp-v8r`), providing userspace initialization and syscall/gate hooks across 1 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[fvp_userspace.c:g_userspace_data]` Module symbol `g_userspace_data`.
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `fvp-armv8r` (`arm64/fvp-v8r`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 3 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[CMakeLists.txt:board]` CMake build target source registration.
