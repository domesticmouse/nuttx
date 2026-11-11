# risc-v

## Overview
Provides RISC-V hardware floating-point implementation of single-precision fused multiply-add (`fmaf`) using the `fmadd.s` instruction.

## Interface
- `lib_fmaf_riscv.c:fmaf`

## Invariants
- Uses `volatile` inline assembly (`fmadd.s`) so the compiler cannot reorder or cache the operation across `fesetround()` and `fetestexcept()` calls or lower `__builtin_fmaf` into a recursive call (`lib_fmaf_riscv.c:fmaf`).

## Side Effects
- Reads the active RISC-V floating-point rounding mode (`frm`) and updates hardware FPU exception flags (`fflags`).

## Verification
- Run: `make test`
