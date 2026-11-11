# include (`nuttx/arch/renesas/include`)

## Overview
Hardware abstraction and architecture package for `include` under `nuttx/arch/renesas/include`, providing 9 header file(s) and 0 source file(s) (including `arch.h`, `inttypes.h`, `irq.h`, `limits.h`).

## Subdirectories & Boundaries
- `m16c`: [./m16c/README.md](./m16c/README.md) - Hardware abstraction and architecture package for `m16c` under `nuttx/arch/renesas/include/m16c`, providing 5 header file(s) and 0 source file(s) (including `arch.h`, `inttypes.h`, `irq.h`, `limits.h`).
- `rx65n`: [./rx65n/README.md](./rx65n/README.md) - Hardware abstraction and architecture package for `rx65n` under `nuttx/arch/renesas/include/rx65n`, providing 6 header file(s) and 0 source file(s) (including `arch.h`, `inttypes.h`, `iodefine.h`, `irq.h`).
- `sh1`: [./sh1/README.md](./sh1/README.md) - Hardware abstraction and architecture package for `sh1` under `nuttx/arch/renesas/include/sh1`, providing 5 header file(s) and 0 source file(s) (including `arch.h`, `inttypes.h`, `irq.h`, `limits.h`).

## Interface
- `[irq.h:STACKFRAME_ALIGN]`
- `[irq.h:up_interrupt_context]`
- `[setjmp.h:setjmp]`
- `[setjmp.h:setjmp_buf_s]`
- `[setjmp.h:jmp_buf]`
- `[sh1Plimits.h:CHAR_BIT]`
- `[sh1Plimits.h:SCHAR_MIN]`
- `[sh1Plimits.h:SCHAR_MAX]`
- `[sh1Plimits.h:UCHAR_MAX]`
- `[sh1Plimits.h:CHAR_MIN]`
- `[sh1Plimits.h:CHAR_MAX]`
- `[sh1Plimits.h:SHRT_MIN]`
- `[sh1Plimits.h:SHRT_MAX]`
- `[sh1Plimits.h:USHRT_MAX]`
- `[sh1Plimits.h:INT_MIN]`
- `[sh1Ptypes.h:_int8_t]`
- `[sh1Ptypes.h:_uint8_t]`
- `[sh1Ptypes.h:_int16_t]`
- `[sh1Ptypes.h:_uint16_t]`
- `[sh1Ptypes.h:_int32_t]`
- `[sh1Ptypes.h:_uint32_t]`
- `[sh1Ptypes.h:_int64_t]`
- `[sh1Ptypes.h:_uint64_t]`
- `[sh1Ptypes.h:irqstate_t]`
- `[sh1Ptypes.h:__INT64_DEFINED]`
- [./m16c/README.md](./m16c/README.md)
- [./rx65n/README.md](./rx65n/README.md)
- [./sh1/README.md](./sh1/README.md)

## Invariants
- `[setjmp.h:#error]` Compile-time guard: setjmp() not compiled!

## Side Effects
- None

## Verification
- Run: `make test`
