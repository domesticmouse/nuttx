# `imxrt1170-evk/kernel` Component (`boards/arm/imxrt/imxrt1170-evk/kernel`)

## Overview
Protected-build userspace/kernel boundary module (`kernel`) for `imxrt1170-evk` (`arm/imxrt`), providing userspace initialization and syscall/gate hooks across 1 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[imxrt_userspace.c:CONFIG_INIT_ENTRYPOINT]` Public function `CONFIG_INIT_ENTRYPOINT()`

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_INIT_ENTRYPOINT`, `CONFIG_INTELHEX_BINARY`, `CONFIG_MOTOROLA_SREC`, `CONFIG_RAW_BINARY`
- `[imxrt_userspace.c:#error]` Compile-time guard: `CONFIG_NUTTX_USERSPACE not defined`
- `[imxrt_userspace.c:#error]` Compile-time guard: `CONFIG_NUTTX_USERSPACE must be 0x30200000 to match user-space.ld`

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh imxrt1170-evk:nsh && make`
