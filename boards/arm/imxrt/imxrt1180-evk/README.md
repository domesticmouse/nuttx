# `imxrt1180-evk` Board Support Package (`boards/arm/imxrt/imxrt1180-evk`)

## Overview
Board Support Package (BSP) blueprint for `imxrt1180-evk` (`arm` / `imxrt`). Coordinates board initialization, headers, and tooling across `include, src, tools`. Includes build configurations: `bl`, `nsh`, `nsh-m33`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `imxrt1180-evk` (`arm/imxrt`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 2 header file(s). Key symbols: `[board.h:GPIO_FLEXSPI_DQS]` Hardware/board configuration macros (`GPIO_FLEXSPI_DQS`, `GPIO_FLEXSPI_SCK`, `GPIO_FLEXSPI_CS`, `GPIO_FLEXSPI_IO0`, `GPIO_FLEXSPI_IO1`, `GPIO_FLEXSPI_IO2` (+49 more)), `[imxrt118x_trdc_config.h:RWX]` Hardware/board configuration macros (`RWX`, `TRDC_FULL_ACCESS_GLBAC`, `DID_CM33`, `DID_EDMA3_RESET`, `DID_CM7`, `DID_USDHC1` (+27 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `imxrt1180-evk` (`arm/imxrt`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 10 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[imxrt1180-evk.h:imxrt_bringup]` Public declaration `imxrt_bringup()`.
- [`tools`](./tools/README.md) - Board support component `tools` for `imxrt1180-evk` (`arm/imxrt`), containing 2 source/script file(s) (`flash-jlink.sh, gdbserver-jlink.sh`). Key symbols: `[flash-jlink.sh]` Shell script entry point `flash-jlink.sh`, `[gdbserver-jlink.sh]` Shell script entry point `gdbserver-jlink.sh`.
