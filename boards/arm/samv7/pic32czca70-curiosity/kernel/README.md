# `pic32czca70-curiosity/kernel` Component (`boards/arm/samv7/pic32czca70-curiosity/kernel`)

## Overview
Protected-build userspace/kernel boundary module (`kernel`) for `pic32czca70-curiosity` (`arm/samv7`), providing userspace initialization and syscall/gate hooks across 1 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[sam_userspace.c]` Translation unit `sam_userspace.c`

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_INIT_ENTRYPOINT`, `CONFIG_INTELHEX_BINARY`, `CONFIG_MOTOROLA_SREC`, `CONFIG_RAW_BINARY`
- `[sam_userspace.c:#error]` Compile-time guard: `CONFIG_NUTTX_USERSPACE not defined`
- `[sam_userspace.c:#error]` Compile-time guard: `CONFIG_NUTTX_USERSPACE must be 0x00500000 to match user-space.ld`

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh pic32czca70-curiosity:nsh && make`
