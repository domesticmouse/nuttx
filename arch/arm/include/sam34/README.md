# sam34 (`nuttx/arch/arm/include/sam34`)

## Overview
Hardware abstraction and architecture package for `sam34` under `nuttx/arch/arm/include/sam34`, providing 8 header file(s) and 0 source file(s) (including `chip.h`, `irq.h`, `sam3u_irq.h`, `sam3x_irq.h`).

## Interface
- `[chip.h:SAM34_FLASH_SIZE]`
- `[chip.h:SAM34_SRAM0_SIZE]`
- `[chip.h:SAM34_SRAM1_SIZE]`
- `[chip.h:SAM34_NFCSRAM_SIZE]`
- `[chip.h:SAM34_NDMACHAN]`
- `[chip.h:SAM34_NPDCCHAN]`
- `[chip.h:SAM34_NMCI2]`
- `[chip.h:SAM34_NSLCD]`
- `[chip.h:SAM34_NAESA]`
- `[chip.h:SAM34_NUDPHS]`
- `[chip.h:SAM34_NUHPHS]`
- `[chip.h:SAM34_NUDPFS]`
- `[irq.h:SAM_IRQ_RESERVED]`
- `[irq.h:SAM_IRQ_NMI]`
- `[irq.h:SAM_IRQ_HARDFAULT]`
- `[irq.h:SAM_IRQ_MEMFAULT]`
- `[irq.h:SAM_IRQ_BUSFAULT]`
- `[irq.h:SAM_IRQ_USAGEFAULT]`
- `[irq.h:SAM_IRQ_SVCALL]`
- `[irq.h:SAM_IRQ_DBGMONITOR]`
- `[irq.h:SAM_IRQ_PENDSV]`
- `[irq.h:SAM_IRQ_SYSTICK]`
- `[irq.h:SAM_IRQ_EXTINT]`
- `[sam3u_irq.h:SAM_PID_SUPC]`
- `[sam3u_irq.h:SAM_PID_RSTC]`
- `[sam3u_irq.h:SAM_PID_RTC]`
- `[sam3u_irq.h:SAM_PID_RTT]`
- `[sam3u_irq.h:SAM_PID_WDT]`
- `[sam3u_irq.h:SAM_PID_PMC]`
- `[sam3u_irq.h:SAM_PID_EEFC0]`

## Invariants
- `[chip.h:#error]` Compile-time guard: Unknown SAM3/4 chip type
- `[irq.h:#error]` Compile-time guard: Unrecognized SAM architecture

## Side Effects
- None

## Verification
- Run: `make test`
