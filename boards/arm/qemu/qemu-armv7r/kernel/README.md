# `qemu-armv7r/kernel` Component (`boards/arm/qemu/qemu-armv7r/kernel`)

## Overview
Protected-build userspace/kernel boundary module (`kernel`) for `qemu-armv7r` (`arm/qemu`), providing userspace initialization and syscall/gate hooks across 1 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[qemu_userspace.c:g_userspace_data]` Module symbol `g_userspace_data`

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_INIT_ENTRYPOINT`, `CONFIG_INTELHEX_BINARY`, `CONFIG_MOTOROLA_SREC`, `CONFIG_RAW_BINARY`
- `[qemu_userspace.c:#error]` Compile-time guard: `CONFIG_NUTTX_USERSPACE not defined`

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh qemu-armv7r:nsh && make`
