# `imxrt1170-evk` Board Support Package (`boards/arm/imxrt/imxrt1170-evk`)

## Overview
Board Support Package (BSP) blueprint for `imxrt1170-evk` (`arm` / `imxrt`). Coordinates board initialization, headers, and tooling across `include, kernel, src`. Includes build configurations: `can`, `canfd`, `knsh`, `libcxxtest`, `netnsh`, `nsh`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `imxrt1170-evk` (`arm/imxrt`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:IMXRT_VDD_SOC]` Hardware/board configuration macros (`IMXRT_VDD_SOC`, `BOARD_XTAL_FREQUENCY`, `IMXRT_PRE_PERIPH_CLK_SEL`, `IMXRT_PERIPH_CLK_SEL`, `IMXRT_ARM_PLL_DIV_SELECT`, `IMXRT_ARM_PODF_DIVIDER` (+90 more)).
- [`kernel`](./kernel/README.md) - Protected-build userspace/kernel boundary module (`kernel`) for `imxrt1170-evk` (`arm/imxrt`), providing userspace initialization and syscall/gate hooks across 1 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[imxrt_userspace.c:CONFIG_INIT_ENTRYPOINT]` Public function `CONFIG_INIT_ENTRYPOINT()`.
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `imxrt1170-evk` (`arm/imxrt`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 23 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[CMakeLists.txt:board]` CMake build target source registration.
