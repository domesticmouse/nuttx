# `arcx-socket-grid` Board Support Package (`boards/arm/imxrt/arcx-socket-grid`)

## Overview
Board Support Package (BSP) blueprint for `arcx-socket-grid` (`arm` / `imxrt`). Coordinates board initialization, headers, and tooling across `include, kernel, src`. Includes build configurations: `nsh`, `usbdisk`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `arcx-socket-grid` (`arm/imxrt`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:IMXRT_VDD_SOC]` Hardware/board configuration macros (`IMXRT_VDD_SOC`, `BOARD_XTAL_FREQUENCY`, `IMXRT_PRE_PERIPH_CLK_SEL`, `IMXRT_PERIPH_CLK_SEL`, `IMXRT_ARM_PLL_DIV_SELECT`, `IMXRT_ARM_PODF_DIVIDER` (+106 more)).
- [`kernel`](./kernel/README.md) - Protected-build userspace/kernel boundary module (`kernel`) for `arcx-socket-grid` (`arm/imxrt`), providing userspace initialization and syscall/gate hooks across 1 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[imxrt_userspace.c:g_userspace_data]` Module symbol `g_userspace_data`.
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `arcx-socket-grid` (`arm/imxrt`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 14 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[CMakeLists.txt:board]` CMake build target source registration.
