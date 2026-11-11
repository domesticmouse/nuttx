# max326xx (`nuttx/arch/arm/include/max326xx`)

## Overview
Hardware abstraction and architecture package for `max326xx` under `nuttx/arch/arm/include/max326xx`, providing 5 header file(s) and 0 source file(s) (including `chip.h`, `irq.h`, `max32620_30_irq.h`, `max32660_irq.h`).

## Interface
- `[chip.h:MAX326_NWDOG]`
- `[chip.h:MAX326_NWWDOG]`
- `[chip.h:MAX326_NRWDOG]`
- `[chip.h:MAX326_NWAKEUP]`
- `[chip.h:MAX326_NRTC]`
- `[chip.h:MAX326_NCRC]`
- `[chip.h:MAX326_NAES]`
- `[chip.h:MAX326_NUSB20]`
- `[chip.h:MAX326_NTMR32]`
- `[chip.h:MAX326_NTMR8]`
- `[chip.h:MAX326_NPTENGINE]`
- `[chip.h:MAX326_NSPIM]`
- `[irq.h:MAX326_IRQ_RESERVED]`
- `[irq.h:MAX326_IRQ_NMI]`
- `[irq.h:MAX326_IRQ_HARDFAULT]`
- `[irq.h:MAX326_IRQ_MEMFAULT]`
- `[irq.h:MAX326_IRQ_BUSFAULT]`
- `[irq.h:MAX326_IRQ_USAGEFAULT]`
- `[irq.h:MAX326_IRQ_SVCALL]`
- `[irq.h:MAX326_IRQ_DBGMONITOR]`
- `[irq.h:MAX326_IRQ_PENDSV]`
- `[irq.h:MAX326_IRQ_SYSTICK]`
- `[irq.h:MAX326_IRQ_EXTINT]`
- `[max32620_30_irq.h:MAX326_IRQ_CRYPTO]`
- `[max32620_30_irq.h:MAX326_IRQ_SUPPLY]`
- `[max32620_30_irq.h:MAX326_IRQ_FLC]`
- `[max32620_30_irq.h:MAX326_IRQ_ALARM0]`
- `[max32620_30_irq.h:MAX326_IRQ_ALARM1]`
- `[max32620_30_irq.h:MAX326_IRQ_INTERVAL]`
- `[max32620_30_irq.h:MAX326_IRQ_RTCOVF]`

## Invariants
- `[chip.h:#error]` Compile-time guard: Unrecognized MAX326XX chip
- `[irq.h:#error]` Compile-time guard: Unsupported MAX326XX family

## Side Effects
- None

## Verification
- Run: `make test`
