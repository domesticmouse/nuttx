# `mps2-an500` Board Support Package (`boards/arm/mps/mps2-an500`)

## Overview
Board Support Package (BSP) blueprint for `mps2-an500` (`arm` / `mps`). Coordinates board initialization, headers, and tooling across `include, kernel, src`. Includes build configurations: `knsh`, `nsh`, `xipfs`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `mps2-an500` (`arm/mps`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:MPS_SYSTICK_CLOCK]` Hardware/board configuration macros (`MPS_SYSTICK_CLOCK`).
- [`kernel`](./kernel/README.md) - Protected-build userspace/kernel boundary module (`kernel`) for `mps2-an500` (`arm/mps`), providing userspace initialization and syscall/gate hooks across 1 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[mps_userspace.c:CONFIG_INIT_ENTRYPOINT]` Public function `CONFIG_INIT_ENTRYPOINT()`.
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `mps2-an500` (`arm/mps`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 2 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[CMakeLists.txt:board]` CMake build target source registration.
