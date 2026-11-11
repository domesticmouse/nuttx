# `common` Board Support Package (`boards/risc-v/mpfs/common`)

## Overview
Board Support Package (BSP) blueprint for `common` (`risc-v` / `mpfs`). Coordinates board initialization, headers, and tooling across `kernel, src`.

## Subdirectories & Boundaries
- [`kernel`](./kernel/README.md) - Protected-build userspace/kernel boundary module (`kernel`) for `common` (`risc-v/mpfs`), providing userspace initialization and syscall/gate hooks across 1 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[mpfs_userspace.c:g_userspace_data]` Module symbol `g_userspace_data`.
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `common` (`risc-v/mpfs`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 8 source file(s). Key symbols: `[Make.defs:CSRCS]` Registered build sources in `Make.defs`, `[mpfs_board_spi.c:mpfs_board_spi_init]` Public function `mpfs_board_spi_init()`.
