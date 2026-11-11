# `common/kernel` Component (`boards/risc-v/mpfs/common/kernel`)

## Overview
Protected-build userspace/kernel boundary module (`kernel`) for `common` (`risc-v/mpfs`), providing userspace initialization and syscall/gate hooks across 1 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[mpfs_userspace.c:g_userspace_data]` Module symbol `g_userspace_data`

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_INIT_ENTRYPOINT`, `CONFIG_INTELHEX_BINARY`, `CONFIG_MOTOROLA_SREC`, `CONFIG_RAW_BINARY`
- `[mpfs_userspace.c:#error]` Compile-time guard: `CONFIG_NUTTX_USERSPACE not defined`

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh sim:nsh && make`
