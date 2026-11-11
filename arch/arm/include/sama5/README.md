# sama5 (`nuttx/arch/arm/include/sama5`)

## Overview
Hardware abstraction and architecture package for `sama5` under `nuttx/arch/arm/include/sama5`, providing 5 header file(s) and 0 source file(s) (including `chip.h`, `irq.h`, `sama5d2_irq.h`, `sama5d3_irq.h`).

## Interface
- `[chip.h:ATSAMA5D2]`
- `[chip.h:SAM_ISRAM0_SIZE]`
- `[chip.h:SAM_ISRAM1_SIZE]`
- `[chip.h:SAM_NDMAC]`
- `[chip.h:SAM_NDMACHAN]`
- `[chip.h:SAM_NQSPI]`
- `[chip.h:ATSAMA5D3]`
- `[sama5d2_irq.h:SAM_PID_FIQ]`
- `[sama5d2_irq.h:SAM_PID_ARM]`
- `[sama5d2_irq.h:SAM_PID_PIT]`
- `[sama5d2_irq.h:SAM_PID_WDT]`
- `[sama5d2_irq.h:SAM_PID_EMAC0]`
- `[sama5d2_irq.h:SAM_PID_XDMAC0]`
- `[sama5d2_irq.h:SAM_PID_XDMAC1]`
- `[sama5d2_irq.h:SAM_PID_ICM]`
- `[sama5d2_irq.h:SAM_PID_AES]`
- `[sama5d2_irq.h:SAM_PID_AESB]`
- `[sama5d2_irq.h:SAM_PID_TDES]`
- `[sama5d2_irq.h:SAM_PID_SHA]`
- `[sama5d3_irq.h:SAM_PID_FIQ]`
- `[sama5d3_irq.h:SAM_PID_SYS]`
- `[sama5d3_irq.h:SAM_PID_DBGU]`
- `[sama5d3_irq.h:SAM_PID_PIT]`
- `[sama5d3_irq.h:SAM_PID_WDT]`
- `[sama5d3_irq.h:SAM_PID_HSMC]`
- `[sama5d3_irq.h:SAM_PID_PIOA]`
- `[sama5d3_irq.h:SAM_PID_PIOB]`
- `[sama5d3_irq.h:SAM_PID_PIOC]`
- `[sama5d3_irq.h:SAM_PID_PIOD]`
- `[sama5d3_irq.h:SAM_PID_PIOE]`

## Invariants
- `[chip.h:#error]` Compile-time guard: Unrecognized SAMAD5 chip
- `[irq.h:#error]` Compile-time guard: Unrecognized SAMA5 family

## Side Effects
- None

## Verification
- Run: `make test`
