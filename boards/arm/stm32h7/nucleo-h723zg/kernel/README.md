# `nucleo-h723zg/kernel` Component (`boards/arm/stm32h7/nucleo-h723zg/kernel`)

## Overview
Protected-build userspace/kernel boundary module (`kernel`) for `nucleo-h723zg` (`arm/stm32h7`), providing userspace initialization and syscall/gate hooks across 1 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[stm32_userspace.c]` Translation unit `stm32_userspace.c`

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_INIT_ENTRYPOINT`, `CONFIG_INTELHEX_BINARY`, `CONFIG_MOTOROLA_SREC`, `CONFIG_RAW_BINARY`
- `[stm32_userspace.c:#error]` Compile-time guard: `CONFIG_NUTTX_USERSPACE not defined`
- `[stm32_userspace.c:#error]` Compile-time guard: `CONFIG_NUTTX_USERSPACE must be 0x08020000 to match memory.ld`

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh nucleo-h723zg:nsh && make`
