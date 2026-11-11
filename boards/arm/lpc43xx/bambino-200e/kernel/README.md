# `bambino-200e/kernel` Component (`boards/arm/lpc43xx/bambino-200e/kernel`)

## Overview
Protected-build userspace/kernel boundary module (`kernel`) for `bambino-200e` (`arm/lpc43xx`), providing userspace initialization and syscall/gate hooks across 1 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[lpc43_userspace.c:g_userspace_data]` Module symbol `g_userspace_data`

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_INIT_ENTRYPOINT`, `CONFIG_INTELHEX_BINARY`, `CONFIG_MOTOROLA_SREC`, `CONFIG_RAW_BINARY`
- `[lpc43_userspace.c:#error]` Compile-time guard: `CONFIG_NUTTX_USERSPACE not defined`
- `[lpc43_userspace.c:#error]` Compile-time guard: `CONFIG_NUTTX_USERSPACE must be 0x14040000 to match memory.ld`

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh bambino-200e:nsh && make`
