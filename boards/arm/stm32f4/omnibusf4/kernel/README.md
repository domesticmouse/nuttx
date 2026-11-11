# `omnibusf4/kernel` Component (`boards/arm/stm32f4/omnibusf4/kernel`)

## Overview
Protected-build userspace/kernel boundary module (`kernel`) for `omnibusf4` (`arm/stm32f4`), providing userspace initialization and syscall/gate hooks across 1 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[stm32_userspace.c:g_userspace_data]` Module symbol `g_userspace_data`

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_INIT_ENTRYPOINT`, `CONFIG_INTELHEX_BINARY`, `CONFIG_MOTOROLA_SREC`, `CONFIG_RAW_BINARY`
- `[stm32_userspace.c:#error]` Compile-time guard: `CONFIG_NUTTX_USERSPACE not defined`
- `[stm32_userspace.c:#error]` Compile-time guard: `CONFIG_NUTTX_USERSPACE must be 0x08020000 to match memory.ld`

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh omnibusf4:nsh && make`
