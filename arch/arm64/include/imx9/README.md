# imx9 (`nuttx/arch/arm64/include/imx9`)

## Overview
Hardware abstraction and architecture package for `imx9` under `nuttx/arch/arm64/include/imx9`, providing 6 header file(s) and 0 source file(s) (including `chip.h`, `imx93_irq.h`, `imx95_irq.h`, `imx9_ahab.h`).

## Interface
- `[chip.h:ARMV8A_DCACHE_LINESIZE]`
- `[chip.h:ARMV8A_ICACHE_LINESIZE]`
- `[chip.h:KB]`
- `[chip.h:MB]`
- `[chip.h:GB]`
- `[chip.h:CONFIG_GICD_BASE]`
- `[chip.h:CONFIG_GICR_BASE]`
- `[chip.h:CONFIG_GICR_OFFSET]`
- `[chip.h:CONFIG_RAMBANK1_ADDR]`
- `[chip.h:CONFIG_RAMBANK1_SIZE]`
- `[imx93_irq.h:IMX9_IRQ_RESERVED32]`
- `[imx93_irq.h:IMX9_IRQ_RESERVED33]`
- `[imx93_irq.h:IMX9_IRQ_RESERVED34]`
- `[imx93_irq.h:IMX9_IRQ_RESERVED35]`
- `[imx93_irq.h:IMX9_IRQ_RESERVED36]`
- `[imx93_irq.h:IMX9_IRQ_RESERVED37]`
- `[imx93_irq.h:IMX9_IRQ_RESERVED38]`
- `[imx93_irq.h:IMX9_IRQ_RESERVED39]`
- `[imx93_irq.h:IMX9_IRQ_CAN1]`
- `[imx93_irq.h:IMX9_IRQ_CAN1_ERROR]`
- `[imx93_irq.h:IMX9_IRQ_GPIO1_0]`
- `[imx93_irq.h:IMX9_IRQ_GPIO1_1]`
- `[imx95_irq.h:IMX9_IRQ_RESERVED16]`
- `[imx95_irq.h:IMX9_IRQ_RESERVED17]`
- `[imx95_irq.h:IMX9_IRQ_RESERVED18]`
- `[imx95_irq.h:IMX9_IRQ_RESERVED19]`
- `[imx95_irq.h:IMX9_IRQ_RESERVED20]`
- `[imx95_irq.h:IMX9_IRQ_RESERVED21]`
- `[imx95_irq.h:IMX9_IRQ_RESERVED22]`
- `[imx95_irq.h:IMX9_IRQ_RESERVED23]`

## Invariants
- `[chip.h:#error]` Compile-time guard: CONFIG_ARM64_GIC_VERSION should be 3 or 4
- `[irq.h:#error]` Compile-time guard: Unrecognized i.MX9 architecture

## Side Effects
- None

## Verification
- Run: `make test`
