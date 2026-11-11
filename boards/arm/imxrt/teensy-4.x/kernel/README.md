# `teensy-4.x/kernel` Component (`boards/arm/imxrt/teensy-4.x/kernel`)

## Overview
Protected-build userspace/kernel boundary module (`kernel`) for `teensy-4.x` (`arm/imxrt`), providing userspace initialization and syscall/gate hooks across 1 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[imxrt_userspace.c:g_userspace_data]` Module symbol `g_userspace_data`

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_INIT_ENTRYPOINT`, `CONFIG_INTELHEX_BINARY`, `CONFIG_MOTOROLA_SREC`, `CONFIG_RAW_BINARY`
- `[imxrt_userspace.c:#error]` Compile-time guard: `CONFIG_NUTTX_USERSPACE not defined`
- `[imxrt_userspace.c:#error]` Compile-time guard: `CONFIG_NUTTX_USERSPACE must be 0x60200000 to match user-space.ld`

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh teensy-4.x:can-4.1 && make`
