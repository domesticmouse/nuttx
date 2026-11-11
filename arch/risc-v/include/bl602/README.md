# bl602 (`nuttx/arch/risc-v/include/bl602`)

## Overview
Hardware abstraction and architecture package for `bl602` under `nuttx/arch/risc-v/include/bl602`, providing 2 header file(s) and 0 source file(s) (including `chip.h`, `irq.h`).

## Interface
- `[irq.h:up_irq_enable]`
- `[irq.h:CLIC_TIMER_ENABLE_ADDRESS]`
- `[irq.h:BL602_IRQ_NUM_BASE]`
- `[irq.h:BL602_IRQ_BMX_ERR]`
- `[irq.h:BL602_IRQ_BMX_TO]`
- `[irq.h:BL602_IRQ_L1C_BMX_ERR]`
- `[irq.h:BL602_IRQ_L1C_BMX_TO]`
- `[irq.h:BL602_IRQ_SEC_BMX_ERR]`
- `[irq.h:BL602_IRQ_RF_TOP_INT0]`
- `[irq.h:BL602_IRQ_RF_TOP_INT1]`
- `[irq.h:BL602_IRQ_SDIO]`
- `[irq.h:BL602_IRQ_DMA_BMX_ERR]`
- `[irq.h:BL602_IRQ_SEC_GMAC]`

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `make test`
