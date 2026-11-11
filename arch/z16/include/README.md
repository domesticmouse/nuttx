# include (`nuttx/arch/z16/include`)

## Overview
Hardware abstraction and architecture package for `include` under `nuttx/arch/z16/include`, providing 6 header file(s) and 0 source file(s) (including `arch.h`, `inttypes.h`, `irq.h`, `limits.h`).

## Subdirectories & Boundaries
- `z16f`: [./z16f/README.md](./z16f/README.md) - Hardware abstraction and architecture package for `z16f` under `nuttx/arch/z16/include/z16f`, providing 3 header file(s) and 0 source file(s) (including `arch.h`, `chip.h`, `irq.h`).

## Interface
- `[inttypes.h:PRId8]`
- `[inttypes.h:PRId16]`
- `[inttypes.h:PRId32]`
- `[inttypes.h:PRIdPTR]`
- `[inttypes.h:PRIi8]`
- `[inttypes.h:PRIi16]`
- `[inttypes.h:PRIi32]`
- `[inttypes.h:PRIiPTR]`
- `[inttypes.h:PRIo8]`
- `[inttypes.h:PRIo16]`
- `[inttypes.h:PRIo32]`
- `[inttypes.h:PRIoPTR]`
- `[irq.h:up_getpc]`
- `[irq.h:up_getsp]`
- `[irq.h:STACKFRAME_ALIGN]`
- `[irq.h:up_interrupt_context]`
- `[irq.h:up_getusrpc]`
- `[irq.h:up_getusrsp]`
- `[limits.h:CHAR_BIT]`
- `[limits.h:SCHAR_MIN]`
- `[limits.h:SCHAR_MAX]`
- `[limits.h:UCHAR_MAX]`
- `[limits.h:CHAR_MIN]`
- `[limits.h:CHAR_MAX]`
- `[limits.h:SHRT_MIN]`
- `[limits.h:SHRT_MAX]`
- `[limits.h:USHRT_MAX]`
- `[limits.h:INT_MIN]`
- `[types.h:_int8_t]`
- `[types.h:_uint8_t]`
- [./z16f/README.md](./z16f/README.md)

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `make test`
