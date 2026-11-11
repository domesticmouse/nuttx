# `qemu-armv7a` Board Support Package (`boards/arm/qemu/qemu-armv7a`)

## Overview
Board Support Package (BSP) blueprint for `qemu-armv7a` (`arm` / `qemu`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `full`, `gdbstub`, `knsh`, `knsh_smp`, `nsh`, `rpproxy` (+2 more).

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `qemu-armv7a` (`arm/qemu`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h]` Board header declarations `board.h`.
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `qemu-armv7a` (`arm/qemu`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 3 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[CMakeLists.txt:board]` CMake build target source registration.
