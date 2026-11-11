# `mr-canhubk3/kernel` Component (`boards/arm/s32k3xx/mr-canhubk3/kernel`)

## Overview
Protected-build userspace/kernel boundary module (`kernel`) for `mr-canhubk3` (`arm/s32k3xx`), providing userspace initialization and syscall/gate hooks across 1 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[s32k3xx_userspace.c:g_userspace_data]` Module symbol `g_userspace_data`

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_INIT_ENTRYPOINT`, `CONFIG_INTELHEX_BINARY`, `CONFIG_MOTOROLA_SREC`, `CONFIG_RAW_BINARY`
- `[s32k3xx_userspace.c:#error]` Compile-time guard: `CONFIG_NUTTX_USERSPACE not defined`
- `[s32k3xx_userspace.c:#error]` Compile-time guard: `CONFIG_NUTTX_USERSPACE must be 0x00501000 to match user-space.ld`

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh mr-canhubk3:nsh && make`
