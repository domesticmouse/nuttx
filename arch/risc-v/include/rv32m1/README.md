# rv32m1 (`nuttx/arch/risc-v/include/rv32m1`)

## Overview
Hardware abstraction and architecture package for `rv32m1` under `nuttx/arch/risc-v/include/rv32m1`, providing 3 header file(s) and 0 source file(s) (including `chip.h`, `irq.h`, `rv32m1ri5cy_irq.h`).

## Interface
- `[rv32m1ri5cy_irq.h:RV32M1_IRQ_MEXT]`
- `[rv32m1ri5cy_irq.h:RV32M1_IRQ_DMA0G0]`
- `[rv32m1ri5cy_irq.h:RV32M1_IRQ_DMA0G1]`
- `[rv32m1ri5cy_irq.h:RV32M1_IRQ_DMA0G2]`
- `[rv32m1ri5cy_irq.h:RV32M1_IRQ_DMA0G3]`
- `[rv32m1ri5cy_irq.h:RV32M1_IRQ_DMA0EER]`
- `[rv32m1ri5cy_irq.h:RV32M1_IRQ_CMC0]`
- `[rv32m1ri5cy_irq.h:RV32M1_IRQ_MUA]`
- `[rv32m1ri5cy_irq.h:RV32M1_IRQ_USB0]`
- `[rv32m1ri5cy_irq.h:RV32M1_IRQ_USDHC0]`
- `[rv32m1ri5cy_irq.h:RV32M1_IRQ_I2S0]`
- `[rv32m1ri5cy_irq.h:RV32M1_IRQ_FLEXIO0]`

## Invariants
- `[irq.h:#error]` Compile-time guard: RV32M1 zeroriscy is not supported yet

## Side Effects
- None

## Verification
- Run: `make test`
