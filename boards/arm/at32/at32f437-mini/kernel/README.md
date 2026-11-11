# `at32f437-mini/kernel` Component (`boards/arm/at32/at32f437-mini/kernel`)

## Overview
Protected-build userspace/kernel boundary module (`kernel`) for `at32f437-mini` (`arm/at32`), providing userspace initialization and syscall/gate hooks across 1 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[at32_userspace.c:g_userspace_data]` Module symbol `g_userspace_data`

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_INIT_ENTRYPOINT`, `CONFIG_INTELHEX_BINARY`, `CONFIG_MOTOROLA_SREC`, `CONFIG_RAW_BINARY`
- `[at32_userspace.c:#error]` Compile-time guard: `CONFIG_NUTTX_USERSPACE not defined`
- `[at32_userspace.c:#error]` Compile-time guard: `CONFIG_NUTTX_USERSPACE must be 0x08060000 to match memory.ld`

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh at32f437-mini:nsh && make`
