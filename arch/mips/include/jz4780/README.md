# jz4780 (`nuttx/arch/mips/include/jz4780`)

## Overview
Hardware abstraction and architecture package for `jz4780` under `nuttx/arch/mips/include/jz4780`, providing 4 header file(s) and 0 source file(s) (including `chip.h`, `cp0.h`, `irq.h`, `irq_jz4780.h`).

## Interface
- `[chip.h:jz_physregaddr]`
- `[chip.h:jz_physramaddr]`
- `[chip.h:jz_virtramaddr]`
- `[chip.h:CKPCR]`
- `[chip.h:CKPCR_CK32CTL_RTCLK]`
- `[chip.h:JZINTC_BASE]`
- `[chip.h:ICMSR0]`
- `[chip.h:ICMCR0]`
- `[chip.h:ICPR0]`
- `[chip.h:ICMSR1]`
- `[chip.h:ICMCR1]`
- `[chip.h:ICPR1]`
- `[chip.h:JZTMR_BASE]`
- `[chip.h:WD_TDR]`
- `[chip.h:WD_TCER]`
- `[cp0.h:CP0_HWRENA_SHIFT]`
- `[cp0.h:CP0_HWRENA_MASK]`
- `[cp0.h:CP0_HWRENA_BIT0]`
- `[cp0.h:CP0_HWRENA_BIT1]`
- `[cp0.h:CP0_HWRENA_BIT2]`
- `[cp0.h:CP0_HWRENA_BIT3]`
- `[cp0.h:CP0_HWRENA_ULR]`
- `[cp0.h:CP0_STATUS_IPL_SHIFT]`
- `[cp0.h:CP0_STATUS_IPL_MASK]`
- `[cp0.h:CP0_INTCTL_VS_SHIFT]`
- `[cp0.h:CP0_INTCTL_VS_MASK]`
- `[cp0.h:CP0_INTCTL_VS_0BYTES]`
- `[irq_jz4780.h:IRQ_OFFSET1]`
- `[irq_jz4780.h:IRQ_VIRTUAL]`
- `[irq_jz4780.h:JZ4780_IRQ_LCD]`

## Invariants
- `[irq.h:#error]` Compile-time guard: Unknown JZ4780 family

## Side Effects
- `[irq.h:__asm__]` Executes inline architecture-specific assembly instructions and barrier operations

## Verification
- Run: `make test`
