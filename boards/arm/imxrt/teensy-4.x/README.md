# `teensy-4.x` Board Support Package (`boards/arm/imxrt/teensy-4.x`)

## Overview
Board Support Package (BSP) blueprint for `teensy-4.x` (`arm` / `imxrt`). Coordinates board initialization, headers, and tooling across `include, kernel, src`. Includes build configurations: `can-4.1`, `enc-4.1`, `lcd-4.1`, `lua-4.1`, `netnsh-4.1`, `nsh-4.0` (+4 more).

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `teensy-4.x` (`arm/imxrt`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:IMXRT_VDD_SOC]` Hardware/board configuration macros (`IMXRT_VDD_SOC`, `BOARD_XTAL_FREQUENCY`, `IMXRT_PRE_PERIPH_CLK_SEL`, `IMXRT_PERIPH_CLK_SEL`, `IMXRT_ARM_PLL_DIV_SELECT`, `IMXRT_ARM_PODF_DIVIDER` (+82 more)).
- [`kernel`](./kernel/README.md) - Protected-build userspace/kernel boundary module (`kernel`) for `teensy-4.x` (`arm/imxrt`), providing userspace initialization and syscall/gate hooks across 1 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[imxrt_userspace.c:g_userspace_data]` Module symbol `g_userspace_data`.
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `teensy-4.x` (`arm/imxrt`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 19 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[CMakeLists.txt:board]` CMake build target source registration.
