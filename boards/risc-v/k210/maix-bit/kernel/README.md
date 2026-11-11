# `maix-bit/kernel` Component (`boards/risc-v/k210/maix-bit/kernel`)

## Overview
Protected-build userspace/kernel boundary module (`kernel`) for `maix-bit` (`risc-v/k210`), providing userspace initialization and syscall/gate hooks across 1 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[k210_userspace.c:g_userspace_data]` Module symbol `g_userspace_data`

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_INIT_ENTRYPOINT`, `CONFIG_INTELHEX_BINARY`, `CONFIG_MOTOROLA_SREC`, `CONFIG_RAW_BINARY`
- `[k210_userspace.c:#error]` Compile-time guard: `CONFIG_NUTTX_USERSPACE not defined`
- `[k210_userspace.c:#error]` Compile-time guard: `CONFIG_NUTTX_USERSPACE must match the value in memory.ld`

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh maix-bit:nsh && make`
