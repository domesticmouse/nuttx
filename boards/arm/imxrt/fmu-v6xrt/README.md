# `fmu-v6xrt` Board Support Package (`boards/arm/imxrt/fmu-v6xrt`)

## Overview
Board Support Package (BSP) blueprint for `fmu-v6xrt` (`arm` / `imxrt`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`, `rptun`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `fmu-v6xrt` (`arm/imxrt`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:BOARD_CPU_FREQUENCY]` Hardware/board configuration macros (`BOARD_CPU_FREQUENCY`, `IMXRT_IPG_PODF_DIVIDER`, `BOARD_GPT_FREQUENCY`, `BOARD_XTAL_FREQUENCY`, `BOARD_FLEXIO_PREQ`, `PIN_USDHC1_D0` (+121 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `fmu-v6xrt` (`arm/imxrt`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 9 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[CMakeLists.txt:board]` CMake build target source registration.
