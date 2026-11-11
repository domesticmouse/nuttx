# include (`nuttx/arch/or1k/include`)

## Overview
Hardware abstraction and architecture package for `include` under `nuttx/arch/or1k/include`, providing 6 header file(s) and 0 source file(s) (including `arch.h`, `inttypes.h`, `irq.h`, `limits.h`).

## Subdirectories & Boundaries
- `mor1kx`: [./mor1kx/README.md](./mor1kx/README.md) - Hardware abstraction and architecture package for `mor1kx` under `nuttx/arch/or1k/include/mor1kx`, providing 1 header file(s) and 0 source file(s) (including `irq.h`).

## Interface
- `[arch.h:arch_addrenv_s]`
- `[arch.h:__PG2SECT_SHIFT]`
- `[arch.h:__PG2SECT_MASK]`
- `[arch.h:ARCH_PG2SECT]`
- `[arch.h:ARCH_SECT2PG]`
- `[arch.h:ARCH_TEXT_NSECTS]`
- `[arch.h:ARCH_DATA_NSECTS]`
- `[arch.h:ARCH_HEAP_NSECTS]`
- `[arch.h:ARCH_SHM_NSECTS]`
- `[arch.h:ARCH_STACK_NSECTS]`
- `[inttypes.h:PRId8]`
- `[inttypes.h:PRId16]`
- `[inttypes.h:PRId32]`
- `[inttypes.h:PRId64]`
- `[inttypes.h:PRIdPTR]`
- `[inttypes.h:PRIi8]`
- `[inttypes.h:PRIi16]`
- `[inttypes.h:PRIi32]`
- `[inttypes.h:PRIi64]`
- `[inttypes.h:PRIiPTR]`
- `[inttypes.h:PRIo8]`
- `[inttypes.h:PRIo16]`
- `[irq.h:STACKFRAME_ALIGN]`
- `[irq.h:up_getusrpc]`
- `[irq.h:up_getusrsp]`
- `[limits.h:CHAR_BIT]`
- `[limits.h:SCHAR_MIN]`
- `[limits.h:SCHAR_MAX]`
- `[limits.h:UCHAR_MAX]`
- `[limits.h:CHAR_MIN]`
- [./mor1kx/README.md](./mor1kx/README.md)

## Invariants
- `[arch.h:#error]` Compile-time guard: Only pages sizes of 4096 are currently supported (CONFIG_ARCH_ADDRENV)

## Side Effects
- `[irq.h:__asm__]` Executes inline architecture-specific assembly instructions and barrier operations
- `[spr.h:__asm__]` Executes inline architecture-specific assembly instructions and barrier operations

## Verification
- Run: `make test`
