# `stm32f746g-disco/kernel` Component (`boards/arm/stm32f7/stm32f746g-disco/kernel`)

## Overview
Protected-build userspace/kernel boundary module (`kernel`) for `stm32f746g-disco` (`arm/stm32f7`), providing userspace initialization and syscall/gate hooks across 1 source file(s).

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
- Run: `./tools/configure.sh stm32f746g-disco:nsh && make`
