# bm3823 (`nuttx/arch/sparc/include/bm3823`)

## Overview
Hardware abstraction and architecture package for `bm3823` under `nuttx/arch/sparc/include/bm3823`, providing 1 header file(s) and 0 source file(s) (including `irq.h`).

## Interface
- `[irq.h:BM3823_IRQ_FIRST]`
- `[irq.h:BM3823_IRQ_RESET]`
- `[irq.h:BM3823_IRQ_INST_ACC_EXCEPTION]`
- `[irq.h:BM3823_IRQ_ILL_INST]`
- `[irq.h:BM3823_IRQ_PRIVELEGE_INST]`
- `[irq.h:BM3823_IRQ_FP_DISABLED]`
- `[irq.h:BM3823_IRQ_WINDOW_OVERFLOW]`
- `[irq.h:BM3823_IRQ_WINDOW_UNDERFLOW]`
- `[irq.h:BM3823_IRQ_ADD_NOT_ALIGNED]`
- `[irq.h:BM3823_IRQ_ADD_FP_EXCEPTION]`
- `[irq.h:BM3823_IRQ_DATA_ACC_EXCEPTION]`
- `[irq.h:BM3823_IRQ_TAG_OVERFLOW]`

## Invariants
- `[irq.h:#error]` Compile-time guard: Unrecognized chip

## Side Effects
- None

## Verification
- Run: `make test`
