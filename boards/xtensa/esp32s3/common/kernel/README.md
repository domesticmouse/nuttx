# `common/kernel` Component (`boards/xtensa/esp32s3/common/kernel`)

## Overview
Protected-build userspace/kernel boundary module (`kernel`) for `common` (`xtensa/esp32s3`), providing userspace initialization and syscall/gate hooks across 1 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[esp32s3_userspace.c:g_userspace_data]` Module symbol `g_userspace_data`

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_DEBUG_LINK_MAP`, `CONFIG_INIT_ENTRYPOINT`, `CONFIG_INTELHEX_BINARY`, `CONFIG_RAW_BINARY`
- `[esp32s3_userspace.c:#error]` Compile-time guard: `CONFIG_NUTTX_USERSPACE not defined`

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh sim:nsh && make`
