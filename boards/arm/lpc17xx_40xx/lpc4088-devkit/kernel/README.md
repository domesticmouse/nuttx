# `lpc4088-devkit/kernel` Component (`boards/arm/lpc17xx_40xx/lpc4088-devkit/kernel`)

## Overview
Protected-build userspace/kernel boundary module (`kernel`) for `lpc4088-devkit` (`arm/lpc17xx_40xx`), providing userspace initialization and syscall/gate hooks across 1 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[lpc17_40_userspace.c:g_userspace_data]` Module symbol `g_userspace_data`

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_INIT_ENTRYPOINT`, `CONFIG_INTELHEX_BINARY`, `CONFIG_MOTOROLA_SREC`, `CONFIG_RAW_BINARY`
- `[lpc17_40_userspace.c:#error]` Compile-time guard: `CONFIG_NUTTX_USERSPACE not defined`
- `[lpc17_40_userspace.c:#error]` Compile-time guard: `CONFIG_NUTTX_USERSPACE must be 0x00040000 to match memory.ld`

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh lpc4088-devkit:nsh && make`
