# `qemu-armv7r` Board Support Package (`boards/arm/qemu/qemu-armv7r`)

## Overview
Board Support Package (BSP) blueprint for `qemu-armv7r` (`arm` / `qemu`). Coordinates board initialization, headers, and tooling across `include, kernel, src`. Includes build configurations: `nsh`, `pnsh`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `qemu-armv7r` (`arm/qemu`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 2 header file(s). Key symbols: `[board.h]` Board header declarations `board.h`, `[board_memorymap.h:QEMU_DDR_BASE]` Hardware/board configuration macros (`QEMU_DDR_BASE`, `QEMU_DDR_SIZE`, `KFLASH_START`, `KFLASH_SIZE`, `KSRAM_START`, `KSRAM_SIZE` (+9 more)).
- [`kernel`](./kernel/README.md) - Protected-build userspace/kernel boundary module (`kernel`) for `qemu-armv7r` (`arm/qemu`), providing userspace initialization and syscall/gate hooks across 1 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[qemu_userspace.c:g_userspace_data]` Module symbol `g_userspace_data`.
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `qemu-armv7r` (`arm/qemu`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 3 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[CMakeLists.txt:board]` CMake build target source registration.
