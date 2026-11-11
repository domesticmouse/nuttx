# minerva (`nuttx/arch/misoc/include/minerva`)

## Overview
Hardware abstraction and architecture package for `minerva` under `nuttx/arch/misoc/include/minerva`, providing 2 header file(s) and 0 source file(s) (including `csrdefs.h`, `irq.h`).

## Interface
- `[csrdefs.h:CSR_MVENDORID_ADDR]`
- `[csrdefs.h:CSR_MARCHID_ADDR]`
- `[csrdefs.h:CSR_MIMPID_ADDR]`
- `[csrdefs.h:CSR_MHARTID_ADDR]`
- `[csrdefs.h:CSR_MSTATUS_ADDR]`
- `[csrdefs.h:CSR_MISA_ADDR]`
- `[csrdefs.h:CSR_MEDELEG_ADDR]`
- `[csrdefs.h:CSR_MIDELEG_ADDR]`
- `[csrdefs.h:CSR_MIE_ADDR]`
- `[csrdefs.h:CSR_MTVEC_ADDR]`
- `[csrdefs.h:CSR_MCOUTEREN_ADDR]`
- `[csrdefs.h:CSR_MSCRATCH_ADDR]`
- `[irq.h:xcpt_syscall_s]`
- `[irq.h:xcptcontext]`
- `[irq.h:MINERVA_NINTERRUPTS]`
- `[irq.h:MINERVA_IRQ_SWINT]`
- `[irq.h:NR_IRQS]`
- `[irq.h:CONFIG_SYS_NNEST]`
- `[irq.h:REG_X0_NDX]`
- `[irq.h:REG_X1_NDX]`
- `[irq.h:REG_X2_NDX]`
- `[irq.h:REG_X3_NDX]`
- `[irq.h:REG_X4_NDX]`
- `[irq.h:REG_X5_NDX]`
- `[irq.h:REG_X6_NDX]`
- `[irq.h:REG_X7_NDX]`

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `make test`
