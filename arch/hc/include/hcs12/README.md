# hcs12 (`nuttx/arch/hc/include/hcs12`)

## Overview
Hardware abstraction and architecture package for `hcs12` under `nuttx/arch/hc/include/hcs12`, providing 3 header file(s) and 0 source file(s) (including `irq.h`, `limits.h`, `types.h`).

## Interface
- `[irq.h:xcptcontext]`
- `[irq.h:HCS12_CCR_C]`
- `[irq.h:HCS12_CCR_V]`
- `[irq.h:HCS12_CCR_Z]`
- `[irq.h:HCS12_CCR_N]`
- `[irq.h:HCS12_CCR_I]`
- `[irq.h:HCS12_CCR_H]`
- `[irq.h:HCS12_CCR_X]`
- `[irq.h:HCS12_CCR_S]`
- `[irq.h:REG_PPAGE]`
- `[irq.h:REG_FIRST_SOFTREG]`
- `[irq.h:REG_SOFTREG1]`
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
- `[types.h:_int16_t]`
- `[types.h:_uint16_t]`
- `[types.h:_int32_t]`
- `[types.h:_uint32_t]`
- `[types.h:_int64_t]`
- `[types.h:_uint64_t]`

## Invariants
- `[irq.h:#error]` Compile-time guard: Need to save more registers

## Side Effects
- `[irq.h:__asm__]` Executes inline architecture-specific assembly instructions and barrier operations

## Verification
- Run: `make test`
