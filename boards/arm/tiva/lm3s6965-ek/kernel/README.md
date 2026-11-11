# `lm3s6965-ek/kernel` Component (`boards/arm/tiva/lm3s6965-ek/kernel`)

## Overview
Protected-build userspace/kernel boundary module (`kernel`) for `lm3s6965-ek` (`arm/tiva`), providing userspace initialization and syscall/gate hooks across 1 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[lm_userspace.c:g_userspace_data]` Module symbol `g_userspace_data`

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_INIT_ENTRYPOINT`, `CONFIG_INTELHEX_BINARY`, `CONFIG_MOTOROLA_SREC`, `CONFIG_RAW_BINARY`
- `[lm_userspace.c:#error]` Compile-time guard: `CONFIG_NUTTX_USERSPACE not defined`
- `[lm_userspace.c:#error]` Compile-time guard: `CONFIG_NUTTX_USERSPACE must be 0x00020000 to match memory.ld`

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh lm3s6965-ek:nsh && make`
