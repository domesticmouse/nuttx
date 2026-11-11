# `smartl-c906/kernel` Component (`boards/risc-v/c906/smartl-c906/kernel`)

## Overview
Protected-build userspace/kernel boundary module (`kernel`) for `smartl-c906` (`risc-v/c906`), providing userspace initialization and syscall/gate hooks across 1 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[c906_userspace.c:g_userspace_data]` Module symbol `g_userspace_data`

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_C906_WITH_QEMU`, `CONFIG_INIT_ENTRYPOINT`, `CONFIG_INTELHEX_BINARY`, `CONFIG_MOTOROLA_SREC`, `CONFIG_RAW_BINARY`
- `[c906_userspace.c:#error]` Compile-time guard: `CONFIG_NUTTX_USERSPACE not defined`
- `[c906_userspace.c:#error]` Compile-time guard: `CONFIG_NUTTX_USERSPACE must match the value in memory.ld`

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh smartl-c906:nsh && make`
