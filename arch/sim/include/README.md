# include (`nuttx/arch/sim/include`)

## Overview
Hardware abstraction and architecture package for `include` under `nuttx/arch/sim/include`, providing 8 header file(s) and 0 source file(s) (including `arch.h`, `elf.h`, `inttypes.h`, `irq.h`).

## Interface
- `[elf.h:EM_ARCH]`
- `[elf.h:EF_FLAG]`
- `[inttypes.h:_PRI64PREFIX]`
- `[inttypes.h:_SCN64PREFIX]`
- `[inttypes.h:INT64_C]`
- `[inttypes.h:UINT64_C]`
- `[inttypes.h:PRId8]`
- `[inttypes.h:PRId16]`
- `[inttypes.h:PRId32]`
- `[inttypes.h:PRId64]`
- `[irq.h:up_irq_flags]`
- `[irq.h:up_irq_save]`
- `[irq.h:up_irq_restore]`
- `[irq.h:up_irq_enable]`
- `[irq.h:xcptcontext]`
- `[irq.h:NR_IRQS]`
- `[irq.h:STACKFRAME_ALIGN]`
- `[irq.h:up_getpc]`
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

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `make test`
