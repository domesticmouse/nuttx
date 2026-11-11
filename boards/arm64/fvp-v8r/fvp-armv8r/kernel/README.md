# `fvp-armv8r/kernel` Component (`boards/arm64/fvp-v8r/fvp-armv8r/kernel`)

## Overview
Protected-build userspace/kernel boundary module (`kernel`) for `fvp-armv8r` (`arm64/fvp-v8r`), providing userspace initialization and syscall/gate hooks across 1 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[fvp_userspace.c:g_userspace_data]` Module symbol `g_userspace_data`

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_INIT_ENTRYPOINT`, `CONFIG_INTELHEX_BINARY`, `CONFIG_MOTOROLA_SREC`, `CONFIG_RAW_BINARY`
- `[fvp_userspace.c:#error]` Compile-time guard: `CONFIG_NUTTX_USERSPACE not defined`
- `[fvp_userspace.c:#error]` Compile-time guard: `CONFIG_NUTTX_USERSPACE must be 0x100000 to match memory.ld`

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh fvp-armv8r:nsh && make`
