# `rv-virt/kernel` Component (`boards/risc-v/qemu-rv/rv-virt/kernel`)

## Overview
Protected-build userspace/kernel boundary module (`kernel`) for `rv-virt` (`risc-v/qemu-rv`), providing userspace initialization and syscall/gate hooks across 1 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[rv_virt_userspace.c:g_userspace_data]` Module symbol `g_userspace_data`

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH_RV32`, `CONFIG_INIT_ENTRYPOINT`, `CONFIG_INTELHEX_BINARY`, `CONFIG_MOTOROLA_SREC`, `CONFIG_RAW_BINARY`
- `[rv_virt_userspace.c:#error]` Compile-time guard: `CONFIG_NUTTX_USERSPACE not defined`

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh rv-virt:nsh && make`
