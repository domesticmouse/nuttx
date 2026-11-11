# `m100pfsevp` Board Support Package (`boards/risc-v/mpfs/m100pfsevp`)

## Overview
Board Support Package (BSP) blueprint for `m100pfsevp` (`risc-v` / `mpfs`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `m100pfsevp` (`risc-v/mpfs`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 2 header file(s). Key symbols: `[board.h:mpfs_boardinitialize]` Public declaration `mpfs_boardinitialize()`, `[board.h:MPFS_EMMC_CLK_MODE]` Hardware/board configuration macros (`MPFS_EMMC_CLK_MODE`, `MPFS_SD_CLOCK_4BIT`, `MPFS_EMMCSD_GPIO`, `MPFS_MSS_EXT_SGMII_REF_CLK`, `MPFS_MSS_COREPLEX_CPU_CLK`, `MPFS_MSS_SYSTEM_CLK` (+5 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `m100pfsevp` (`risc-v/mpfs`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 3 source file(s). Key symbols: `[Make.defs:CSRCS]` Registered build sources in `Make.defs`, `[board_config.h:mpfs_bringup]` Public declaration `mpfs_bringup()`.
