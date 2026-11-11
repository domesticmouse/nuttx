# `mps2-an500/kernel` Component (`boards/arm/mps/mps2-an500/kernel`)

## Overview
Protected-build userspace/kernel boundary module (`kernel`) for `mps2-an500` (`arm/mps`), providing userspace initialization and syscall/gate hooks across 1 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[mps_userspace.c:CONFIG_INIT_ENTRYPOINT]` Public function `CONFIG_INIT_ENTRYPOINT()`

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_INIT_ENTRYPOINT`, `CONFIG_INTELHEX_BINARY`, `CONFIG_MOTOROLA_SREC`, `CONFIG_RAW_BINARY`
- `[mps_userspace.c:#error]` Compile-time guard: `CONFIG_NUTTX_USERSPACE not defined`
- `[mps_userspace.c:#error]` Compile-time guard: `CONFIG_NUTTX_USERSPACE must be 0x20000000 to match user-space.ld`

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh mps2-an500:nsh && make`
